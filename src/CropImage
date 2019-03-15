
from __future__ import print_function
import os
from os.path import dirname,join,abspath

import matplotlib.pyplot as plt
import cv2
import numpy as np
import sys

img_dir = abspath(join(dirname(dirname(__file__)), "input"))
out_dir =abspath(join(dirname(dirname(__file__)), "output"))

for img_file in os.listdir(img_dir):
    img_path = abspath(join(img_dir, img_file))
    Outputimg_path = abspath(join(out_dir, img_file))

    try:
        myimg = cv2.imread(img_path,0)  # import image
        h,w = myimg.shape
        prev_mean = 0
        prev_roi = myimg[0:]
        column12 = column22 = 0
        mean12 = mean22 = 0

        #Finding left column of crop
        y = h
        for x in range(0, int(w * 0.1)):
            roi = myimg[0:h, x:x + 1]
            if np.mean(roi) <= 90:
                column1 = x
                mean1 = np.mean(roi)
 
       #Finding left 2nd column of crop to avoid crop actual image
        for x in range(int(w * 0.1), int(w*0.4)):
            roi = myimg[0:h, x:x +1]

            if np.mean(roi) <=100:
                #print("mean", np.mean(roi))
                column12 = x
                mean12 = np.mean(roi)
                next_roi = myimg[0:h,x+1:x+2]
                if np.mean(next_roi) > 100:
                    break
                    
        #Finding right column of crop
        for x in range(int(w*0.8),w):
            roi = myimg[0:h, x:x + 1]
            if np.mean(roi) <= 90:
                #print("mean", np.mean(roi))
                column2 = x
                mean2 = np.mean(roi)

                next_roi = myimg[0:h, x + 1:x + 2]
                if np.mean(next_roi) > 100:
                    break
       #Finding right 2nd column of crop to avoid crop actual image                    
        for x in range(int(w*0.75),int(w*0.95)):
            roi = myimg[0:h, x:x+1]
            if  np.mean(roi) <= 100:
                column22 = x
                mean22 = np.mean(roi)

                next_roi = myimg[0:h, x + 1:x + 2]
                if np.mean(next_roi) > 100:
                    break
        
        x = w
        y= 0
        
        #Finding top row of crop
        for y in range(h-int(h * 0.05),h):
            roi = myimg[y:y+1, 0:x]
            if np.mean(roi) <= 90:
                row1 = y
                next_roi = myimg[y+1:y+2, 0:x]

                if np.mean(next_roi) < 80:
                    break
        roi = myimg[h-int(h*0.99):h-int(h*0.9), 0:x]
        row2=0
        
        #Finding bottom row of crop        
        for y in range(h-int(h * 0.999), h-int(h*0.9)):
            roi = myimg[y:y+1, 0:x]

            if np.mean(roi) <= 90:
                    row2 = y
                    next_roi = myimg[y+1:y+2, 0:x]
                    if np.mean(next_roi) > 100:
                        #print("row",row2)
                        break

        cv2.rectangle(myimg, (column1-1, h), (column1+1,0), (255, 0, 0), 2)
        cv2.rectangle(myimg, (column2-1, h), (column2+1,0), (255, 0, 0), 2)

        cv2.rectangle(myimg, (column12-1, h), (column12+1,0), (160, 0, 0), 2)
        cv2.rectangle(myimg, (column22-1, h), (column22+1,0), (160, 0, 0), 2)

        paper = myimg[row2:row1+5, column1:column2+1]
        if column12 == 0:
            column12 = column1
        if column22 == 0:
            column22 = column2
        paper2 = myimg[row2:row1+5, column12:column22+1]
        cv2.imwrite(Outputimg_path,paper2)

    except Exception as e:
        exc_type, exc_obj, tb = sys.exc_info()
        f = tb.tb_frame
        lineno = tb.tb_lineno
        #print(lineno, ":", e)

for img_file in os.listdir(out_dir):
    os.system('start '+
              abspath(join(out_dir, img_file)))
 
