# 树莓派3B GPIO操作 之 LED流水灯

接下来进行流水灯操作

#### 1、接线，确定GPIO口
我选择如下GPIO口 21、26、19、13和6五个接口

![](https://i.imgur.com/AsYoZmL.jpg)

> 最好每个都测试一下，用上一篇博客点亮LED等代码，修改一下pin即可运行测试。

#### 2、接下来就是写流水灯的代码
   
	import RPi.GPIO as GPIO
	import sys
	import time

	class Led():
	    def __init__(self):
	        self.led_pin = [21,26,19,13,6]
	        GPIO.setmode(GPIO.BCM);
	        GPIO.setwarnings(False)
	        for i in self.led_pin:
	            GPIO.setup(i,GPIO.OUT)
	            GPIO.output(i,GPIO.LOW)
	
	    def on(self,status):
	        GPIO.output(status,GPIO.HIGH)
	
	    def off(self,status):
	        GPIO.output(status,GPIO.LOW)
	
	    def flow(self):
	        while(1):
	            for i in self.led_pin:
	                self.on(i)
	                time.sleep(0.3)
	                self.off(i)
	
	    def off_all(self):
	        for i in self.led_pin:
	            self.off(i)

	def main(status):
   	 	led = Led()
    	if status == 'on':
        	led.flow()
   		elif status == 'off':
        	led.off_all()

	if __name__ == '__main__':
    	main(sys.argv[1])
        
     
代码 主要是flow（）这个方法来实现流水灯，然后off_all()方法是让led全部关闭

#### 3. 效果
![](https://i.imgur.com/BPPJW8i.jpg)

