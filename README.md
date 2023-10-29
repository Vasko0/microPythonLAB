# microPythonLAB

[Симулятор RaspberyPi](https://wokwi.com/projects/379923617507687425)
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
### Бібліотеки
* `from machine import Pin` підключення бібліотеки для роботи з GPIO
* `from utime import sleep` підключення бібліотеки для роботи з затримкою

```python
Pin("Номер GPIO", "Режим роботи GPIO")
```
### Режими роботи GPIO
* `Pin.OUT` режим виведення (контак керує перифірією), наприклад керує світлодіодом
* `Pin.IN` режим введення (контак приймає сигнал), наприклад отримує сигнали з датчиків

### Керування GPIO
* `Pin(5, Pin.OUT).on()` вмикає подачу сигналу/сруму на 5-ий GPIO
* `Pin(5, Pin.OUT).off()` вимикає подачу сигналу/сруму на 5-ий GPIO
* `Pin(5, Pin.OUT).toggle()` переключити сигнал (якщо був вимкнений то ввімкне і навпаки)
* `sleep("час в секундах")` створює затримку в роботі програми на вказану кількість


### Світлодіоди
Підключаються послідовно з резистором 
Важлива полярність, тобто світлодіод, як і будь який інший світлодіод пропускає струм лиш в одному напрямку. Обов'язково підключати мінус до мінуса, плюс до плюса 
## Завдання
Світлодіоди підключити до виводів 1-5
Для завдання номінали резисторів вибирати 100 Ом

1) Вмикати світлодіоди по черзі від 1 до 5
2) Вмикати світлодіоди по черзі від 5 до 1
3) Вмикати світлодіоди по черзі від середини: 3 > 2,4 > 1,5
4) Вмикати світлодіоди по черзі від крайніх: 1,5 > 2,4 > 3
5) Створити світлофор з 3-ох світлодіодів
