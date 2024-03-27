Display Acceleration Visuals
======================
In this activity, you will display the visuals depending on the acceleration data received from the sensor.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/11144308/AA1.gif" width = "100%" height = "50%">




Follow the given steps to complete this activity.




1. Show effect of acceleration by checking the g-force from the sensor data.
   
   ~~~python
    if (topic == "/Gforce"):
        if(float(sensorData["/Gforce"]) > thresholds['gforceMax']):
            images[3] = outsideRangeImages[3]
        else:
             images[3] = inRangeImages[3]
   ~~~




* Save and run the code to check the output.
