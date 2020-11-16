# [Back](https://github.com/ifanzilka/Robo_R2-D2)

## 1. OC 
На саму плату было предустановлена система Lunix (Заточенная) по Paspberry Pi 4

https://www.raspberrypi.org/

Для начала когда мы только вошли нам нужно создать пользователей чтобы они могли добавляться удаленно

Делается это командой `sudo adduser bmarilli`

## 2. Сделали удаленный доступ к нему в рамках одной сети


Смотрим наш ip адресс `ifconfig`

SSH - сервис который позволяет делать удаленный доступ

Если он не установлен устанавливаем командой `sudo apt-get install openssh-server`

 
`ssh 192.168.10.12` команда которая позволяет подключиться к другому компьютеру удаленно

 Но для начала нужно на удаленном компьютере открыть этот доступ 
 
 `service ssh status` Смотрим наш статутс
 
 Если он не запущен запускаем `service ssh status`
 
 Подключение по пользователю `bmarilli@192.168.1.1`
 
 `uname -u` имя нашего пользователя
 
 `w` кто сейчас залогинился
 
  Также по SSH можно поключаться с приложений на андроид и IOS(Shelly)

 ##  3.Первая программа 
 
 Python3 Как правило предустановлен
 
 Теперь установим утилиту pip для установки различных библиотек python -> `sudo apt-get install python3-pip`
 
 Для управления платой нам нужна библиотека GPIO Устанавливаем -> `sudo apt-get install rpi.gpio`

Теперь можем написать полноценную программу для включения-выключения лампочки на плате

     import RPi.GPIO as GPIO
     import time
     GPIO.setmode(GPIO.BCM)
     GPIO.setwarnings(False)
     GPIO.setup(17,GPIO.OUT)
     i = 0
     while (i < 10):
       print("led on")
       GPIO.output(17, GPIO.HIGH)
       time.sleep(1)
       print("led off")
       GPIO.output(17, GPIO.LOW)
       time.sleep(1)
       i = i + 1
    print("end")  
