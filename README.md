# face-detection
i have OS MACOS 
first: I install python 3.9 i writ in the terminal pip3 install python3.9
then I install Opencv 
then I install the IDE for python I use pycharm 
the I write  code from this project  https://www.hackster.io/mjrobot/real-time-face-recognition-an-end-to-end-project-a10826
import numpy as np
import cv2
faceCascade = cv2.CascadeClassifier('Cascades/haarcascade_frontalface_default.xml')#"""Ican,t use thise lin the i have error the i fixid just chang with faceCascade=cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_frontalface_default.xml")"""#

cap = cv2.VideoCapture(0)
cap.set(3,640) # set Width
cap.set(4,480) # set Height
while True:
    ret, img = cap.read()
   # img = cv2.flip(img, -1)## i don,t need this to flip the cam
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = faceCascade.detectMultiScale(
        gray,     
        scaleFactor=1.2,
        minNeighbors=5,     
        minSize=(20, 20)
    )
    for (x,y,w,h) in faces:
        cv2.rectangle(img,(x,y),(x+w,y+h),(255,0,0),2)
        roi_gray = gray[y:y+h, x:x+w]
        roi_color = img[y:y+h, x:x+w]  
    cv2.imshow('video',img)
    k = cv2.waitKey(30) & 0xff
    if k == 27: # press 'ESC' to quit
        break
cap.release()
cv2.destroyAllWindows()

<img width="1047" alt="Screen Shot 1442-11-27 at 5 37 44 PM" src="https://user-images.githubusercontent.com/56722657/125148982-cb4d6100-e13e-11eb-9f08-7cdbc4f27131.png">
