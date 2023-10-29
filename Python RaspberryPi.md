
raspbery pi
https://uk.wikipedia.org/wiki/Raspberry_Pi
**Raspberry Pi** (читається як _Ра́збері па́й_; буквально: [укр.](https://uk.wikipedia.org/wiki/%D0%A3%D0%BA%D1%80%D0%B0%D1%97%D0%BD%D1%81%D1%8C%D0%BA%D0%B0_%D0%BC%D0%BE%D0%B2%D0%B0 "Українська мова") _малиновий пиріг_) — [одноплатний комп'ютер](https://uk.wikipedia.org/wiki/%D0%9E%D0%B4%D0%BD%D0%BE%D0%BF%D0%BB%D0%B0%D1%82%D0%BD%D0%B8%D0%B9_%D0%BA%D0%BE%D0%BC%D0%BF%27%D1%8E%D1%82%D0%B5%D1%80 "Одноплатний комп'ютер"), розроблений британським фондом Raspberry Pi Foundation. Головне призначення — сприяти вивченню базових комп'ютерних навичок школярами.
![[pi-family.webp]]
![[Pasted image 20231026165539.png]]
![[Pasted image 20231026165824.png]]
![[obsidian_git/UzNU/Media/cartoon-pi-connected_image_0.webp]]
**Інтерфейс [введення/виведення](https://uk.wikipedia.org/wiki/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%BD%D1%8F/%D0%B2%D0%B8%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%BD%D1%8F "Введення/виведення") загального призначення** ([англ.](https://uk.wikipedia.org/wiki/%D0%90%D0%BD%D0%B3%D0%BB%D1%96%D0%B9%D1%81%D1%8C%D0%BA%D0%B0_%D0%BC%D0%BE%D0%B2%D0%B0 "Англійська мова") _General-purpose input/output_, GPIO) — інтерфейс для зв'язку між компонентами комп'ютерної системи, наприклад, [мікропроцесором](https://uk.wikipedia.org/wiki/%D0%9C%D1%96%D0%BA%D1%80%D0%BE%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D0%BE%D1%80 "Мікропроцесор") і різними [периферійними пристроями](https://uk.wikipedia.org/wiki/%D0%9F%D0%B5%D1%80%D0%B8%D1%84%D0%B5%D1%80%D1%96%D0%B9%D0%BD%D0%B8%D0%B9_%D0%BF%D1%80%D0%B8%D1%81%D1%82%D1%80%D1%96%D0%B9 "Периферійний пристрій"). Контакти GPIO можуть діяти і як входи, і як виходи, і це, як правило, підлягає налаштуванню. GPIO контакти часто групуються в [порти](https://uk.wikipedia.org/wiki/%D0%9F%D0%BE%D1%80%D1%82_%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%83 "Порт протоколу").

GPIO контакти не мають спеціального призначення і зазвичай залишаються невикористаними. Ідея полягає в тому, що іноді системному інтегратору для побудови повної системи, яка використовує [чип](https://uk.wikipedia.org/wiki/%D0%9C%D1%96%D0%BA%D1%80%D0%BE%D1%81%D1%85%D0%B5%D0%BC%D0%B0 "Мікросхема"), може виявитися корисним мати кілька додаткових ліній цифрового управління. З них можна організувати додаткові схеми, які інакше довелося б створювати з нуля.
![[obsidian_git/cartoon-pi-connected_image_0.webp]]
![[Raspberry-GPIO.jpg]]



```sh
$ pinout
```

Підібрати резистор
![[закон ома.jpg]]
The 3v3 supply pin on the early Raspberry Pi had a maximum available current of about 50 mA and 16 mA per pin. Enough to power a couple of LEDs or a microprocessor, but not much more.
All Raspberry Pi since the Model B+ can provide quite a bit more, up to 500mA to remain on the safe side, thanks to a switching regulator.


![[LedPinout.jpg]]
[Бібліотека micropython](https://docs.micropython.org/en/latest/library/machine.Pin.html)

```bash
$ sudo apt install python
$ sudo apt install python-rpi.gpio python3-rpi.gpio
$ sudo apt install python-gpiozero
```

## Micropython
```python
from machine import Pin
from utime import sleep

print("Hello, Pi Pico!")

led = Pin(5, Pin.OUT)
led2 = Pin(9, Pin.OUT)
while True:
  led2.toggle()
  led.on()  # led.high()
  sleep(0.5)
  led.off() # led.low()
  sleep(0.5)
  

```
## RPi
```python
import RPi.GPIO as GPIO # Import Raspberry Pi GPIO library
from time import sleep # Import the sleep function from the time module

print("Hello World")

GPIO.setwarnings(False) # Ignore warning for now
GPIO.setmode(GPIO.BOARD) # Use physical pin numbering GPIO.BCM for GPIO#
GPIO.setup(8, GPIO.OUT) # Set pin 8 to be an output pin and set initial value to low (off)
while True: # Run forever
  GPIO.output(8, GPIO.HIGH) # Turn on
  sleep(1) # Sleep for 1 second
  GPIO.output(8, GPIO.LOW) # Turn off
  sleep(1) # Sleep for 1 second

```

![[led-blink.gif]]

```bash
python blinking_led.py
```

