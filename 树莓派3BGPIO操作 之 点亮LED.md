#树莓派3B的GPIO操作--点亮LED

直接开始吧，一些准备工作就不在这里详细细说了，比如说，SSH、一些杜邦线呀，面包板呀等等，自己把线接好。

好了，直接开始上代码啦！

1.新建led.py文件，并输入以下代码
    
    import RPi.GPIO as GPIO
    import sys
    import time
    
    class Led():
    	def __init__(self):
    	self.led_pin = 21
    	GPIO.setmode(GPIO.BCM)
    	GPIO.setwarnings(False)
    	GPIO.setup(self.led_pin,GPIO.OUT)
    	GPIO.output(self.led_pin,GPIO.LOW)
    
   	 	def on(self):
    		GPIO.output(self.led_pin,GPIO.HIGH)
    		print('LED-ON')
    
    	def off(self):
    		GPIO.output(self.led_pin,GPIO.LOW)
    		print('LED-OFF')
    
    
    def main(status):
    	led = Led()
    	if status == 'on':
    		led.on()
   		elif status == 'off':
    		led.off()
    
    if __name__ == '__main__':
    	main(sys.argv[1])

   
代码比较简单，就是通过main方法用户输入on 还是off ，然后判断led的开和关闭。

2.运行
> python led.py on
> python led.py off


![](https://i.imgur.com/kxUHw1Z.jpg)


3.效果
![](https://i.imgur.com/zXKlbAJ.jpg)