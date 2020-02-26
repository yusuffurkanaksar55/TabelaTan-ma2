    import cv2
    import numpy as np


    kamera=cv2.VideoCapture(0)


    while True:
        _,kare=kamera.read()
        hsv=cv2.cvtColor(kare,cv2.COLOR_BGR2HSV)
        
        lower_red=np.array([100,100,100])
        upper_red=np.array([130,255,255])
        mask=cv2.inRange(hsv,lower_red,upper_red)
        kernel=np.ones((5,5),np.uint8)
        mask=cv2.erode(mask,kernel)
        
        contours, hierarchy = cv2.findContours(mask, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
        for cnt in contours:
            area=cv2.contourArea(cnt)
            approx=cv2.approxPolyDP(cnt,0.01*cv2.arcLength(cnt,True),True)
            x=approx.ravel()[0]
            y=approx.ravel()[1]
            
            if area>400:
                cv2.drawContours(kare,[approx],0,(0,0,0),5)
                if len(approx)==4:
                    print("Its a rectangle")
        
            
        cv2.imshow("Ekran",kare)
        cv2.imshow("Mask",mask)
        key=cv2.waitKey(1)
        if key==27:
            break
    kamera.release()
    cv2.destroyAllWindows(5)
