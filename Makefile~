DEVICE     = atmega328p
PROGRAMMER = arduino
PORT	   = /dev/ttyACM0
BAUD       = 9600
FILENAME   = main
COMPILE    = avr-gcc -g -mmcu=$(DEVICE)

all: build upload clean

build:
	$(COMPILE) -Os -c $(FILENAME).c -o $(FILENAME).o
	$(COMPILE) -o $(FILENAME).elf $(FILENAME).o
	avr-objcopy -j .text -j .data -O ihex $(FILENAME).elf $(FILENAME).hex

upload:
	avrdude -c $(PROGRAMMER) -p $(DEVICE) -P $(PORT) -U flash:w:$(FILENAME).hex 

clean:
	rm main.o
	rm main.elf
	rm main.hex
