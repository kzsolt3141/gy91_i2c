MCU=atmega8
F_CPU=8000000
CC=avr-gcc
OBJCOPY=avr-objcopy
MEMCHECK=avr-size
IFLAGS=-I../ -I../uart -I../twi -I../mpu9250_i2c -I../bmp280_i2c

CFLAGS=-std=c11 -Wall -g -O3 -mmcu=${MCU} -DF_CPU=${F_CPU} ${IFLAGS}
TARGET=main
SRCS=main.c ../mpu9250_i2c/MPU9250.c ../bmp280_i2c/BMP280.c ../uart/uart.c ../twi/twi.c

all:
	${CC} ${CFLAGS} -o ${TARGET}.bin ${SRCS}
	${OBJCOPY} -j .text -j .data -O ihex ${TARGET}.bin ${TARGET}.hex
	${MEMCHECK} -C --mcu=${MCU} ${TARGET}.bin

clean:
	rm -f *.bin *.hex