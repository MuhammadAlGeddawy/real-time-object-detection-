#!/usr/bin/env python3
import rospy
from std_msgs.msg import Float32
import cv2
import os
import tensorflow as tf
from tensorflow.keras.preprocessing import image
import matplotlib.pyplot as plt 
import numpy as np
from cv_bridge import CvBridge, CvBridgeError
import sys
from tensorflow.keras.models import load_model



rospy.init_node('your node name', anonymous=True)
pub = rospy.Publisher("/obj_class", Float32, queue_size=10)
model_path = 'Saved model path (.h5 File)'
def object():
    model = tf.keras.models.load_model(model_path, compile=False)
    
    
    path="path of captured images"
    i=0

    for img in os.listdir(path):
        img=image.load_img(path+"/"+img,target_size=(224,224))
        plt.imshow(img)
        plt.show()
        
        x=image.img_to_array(img)
        x=np.expand_dims(x,axis=0)
        images=np.vstack([x])
        pred=  model.predict(images,batch_size=1) 

        obj_type = pred[0][0]

        if obj_type<0.5:
            category="your object1 name"
            print("This is a ", category)
            pub.publish(obj_type)

        elif obj_type>0.5:
            category="your object2 name"
            print("This is a ", category)
            pub.publish(obj_type)

 
    
if __name__  == "__main__":
    object()
