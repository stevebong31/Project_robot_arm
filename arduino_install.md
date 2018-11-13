Aruduino install in Ubuntu
=============

https://www.arduino.cc/en/Guide/Linux


아두이노 포트가 인식 안될 경우

<pre><code>
ls -l /dev/ttyACM*

sudo usermod -a -G dialout <username>
sudo chmod a+rw /dev/ttyACM0
  
</code></pre>
