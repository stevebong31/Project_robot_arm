arduino multi servo control
=============


<pre><code>

#if (ARDUINO >= 100)
 #include <Arduino.h>
#else
 #include <WProgram.h>
#include "std_msgs/MultiArrayLayout.h"
#include "std_msgs/MultiArrayDimension.h"

#include "std_msgs/UInt16MultiArray.h"

ros::NodeHandle  nh;

Servo servo1;
Servo servo2;
Servo servo3;

void servo_cb( const std_msgs::UInt16MultiArray&  cmd_msg){
  servo1.write(cmd_msg.data[0]); //set servo angle, should be from 0-180  
  servo2.write(cmd_msg.data[1]); 
  servo3.write(cmd_msg.data[2]); 
  digitalWrite(13, HIGH-digitalRead(13));  //toggle led  
}

#endif

#include <Servo.h> 
#include <ros.h>

ros::Subscriber<std_msgs::UInt16MultiArray> sub("servo", servo_cb);

void setup(){
  pinMode(13, OUTPUT);

  nh.initNode();
  nh.subscribe(sub);


  servo1.attach(9); //attach it to pin 9
  servo2.attach(10);//attach it to pin10
  servo3.attach(11);//attach it to pin11
}

void loop(){
  nh.spinOnce();
  delay(1);
}
</code></pre>

