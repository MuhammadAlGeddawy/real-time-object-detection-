#if (ARDUINO >= 100)
 #include <Arduino.h>
#else
 #include <WProgram.h>
#endif

#include "Wire.h"
#include <ros.h>
#include <std_msgs/String.h>
#include <std_msgs/Float32.h>

//std_msgs::String imu_msg;
ros::NodeHandle  nh;

float value;
void callback( const std_msgs::Float32& msg){
  value = msg.data;
 // Serial.print(value);
  if (value > 0.5) {
    digitalWrite(9, HIGH);
    digitalWrite(6, LOW);
    }
    
  if (value < 0.5) {
    digitalWrite(6, HIGH);
    digitalWrite(9, LOW);
      
    } 
  }

ros::Subscriber<std_msgs::Float32> sub("obj_class", &callback);

void setup() {
  // put your setup code here, to run once:
  nh.initNode();
  nh.subscribe(sub);

  pinMode(9, OUTPUT);
  pinMode(11, OUTPUT);
  nh.initNode();
  nh.subscribe(sub);
 
}

long publisher_timer;

void loop() {
  // put your main code here, to run repeatedly:  

    nh.spinOnce();
    delay(1000);
  }
