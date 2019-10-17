# OpenCV program Edge detection in real time 
# import libraries of python OpenCV  
# where its functionality resides 
import cv2  
import matplotlib.pyplot as plt
from  matplotlib.pyplot import *
import numpy as np
import random
# np is an alias pointing to numpy library 
import numpy as np 

# capture frames from a camera 
cap = cv2.VideoCapture(0) 
  
  
# loop runs if capturing has been initialized 
while(1): 
  
    # reads frames from a camera 
    ret, frame = cap.read() 
  
    # converting BGR to HSV 
    hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV) 
      
    # define range of red color in HSV 
    lower_red = np.array([30,150,50]) 
    upper_red = np.array([255,255,180]) 
      
    # create a red HSV colour boundary and  
    # threshold HSV image 
    mask = cv2.inRange(hsv, lower_red, upper_red) 
  
    # Bitwise-AND mask and original image 
    res = cv2.bitwise_and(frame,frame, mask= mask) 
  
    # Display an original image 
    cv2.imshow('Original',frame) 
  
    # finds edges in the input image image and 
    # marks them in the output map edges 

    
    #laplacien
    k_lap_positif = np.array(([0,1,0],[1,-4,1],[0,1,0]),np.float32)
    k_lap_negatif = np.array(([0,-1,0],[-1,4,-1],[0,-1,0]),np.float32)
    #filter2d
    output_k_lap_positif = cv2.filter2D(cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY),-1,k_lap_positif)
    output_k_lap_negatif = cv2.filter2D(cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY),-1,k_lap_negatif)

    #Prewitt’s
    kprewitt_x = np.array(([1,0,-1],[1,0,-1],[1,0,-1]),np.float32)
    kprewitt_y = np.array(([1,1,1],[0,0,0],[-1,-1,-1]),np.float32)  
    #filter2d
    output_kprewitt_x = cv2.filter2D(cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY),-1,kprewitt_x)
    output_kprewitt_y = cv2.filter2D(cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY),-1,kprewitt_y)

    #Canny
    # Display edges in a frame
    edges = cv2.Canny(frame,100,200)

    #display 
    cv2.imshow('laplacien positif',output_k_lap_positif)
    cv2.imshow('laplacien negatif',output_k_lap_negatif)

    cv2.imshow('laplacien prewit x',output_kprewitt_x) 
    cv2.imshow('laplacien prewit y',output_kprewitt_y)

    cv2.imshow('Canny ',edges) 

    # Wait for Esc key to stop 
    k = cv2.waitKey(5) & 0xFF
    if k == 27: 
        break
  
# Close the window 
cap.release() 
  
# De-allocate any associated memory usage 
cv2.destroyAllWindows()  
#rida_benbouziane
