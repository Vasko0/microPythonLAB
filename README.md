# microPythonLAB

[Симулятор RaspberyPi](https://wokwi.com/projects/300504213470839309)
```python
from machine import Pin
from utime import sleep


led = Pin(5, Pin.OUT)
while True:
  led.on()
  sleep(0.5)
  led.off()
  sleep(0.5)
```

`from machine import Pin` підключення бібліотеки для роботи з GPIO

`from utime import sleep` підключення бібліотеки для роботи з затримкою
```python
Pin("Номер GPIO", "Режим роботи GPIO")
```
Режими роботи GPIO
* `Pin.OUT` режим виведення (контак керує перифірією), наприклад керує світлодіодом
* `Pin.IN` режим введення (контак приймає сигнал), наприклад отримує сигнали з датчиків

`Pin(5, Pin.OUT).on()` вмикає подачу сигналу/сруму на 5-ий GPIO

`Pin(5, Pin.OUT).off()` вимикає подачу сигналу/сруму на 5-ий GPIO

`Pin(5, Pin.OUT).toggle()` переключити сигнал (якщо був вимкнений то ввімкне і навпаки)

`sleep("час в секундах")` створює затримку в роботі програми на вказану кількість
