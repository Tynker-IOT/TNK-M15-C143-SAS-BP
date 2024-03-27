Display Visuals Based on the Sensor Data
======================
In this activity, you will display the visuals depending on the data received from the sensor.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/11130898/C143_obv_3.gif" width = "100%" height = "50%">




Follow the given steps to complete this activity.




1. Create an array to store the images by creating an empty array.
   ~~~python
    images = ["","",""]
   ~~~
2. Show effect of temperature by checking the temperature from the sensor data..
   
   ~~~python
    def on_message(client, userdata, msg):
        global sensorData, images
        if (topic == "/Temperature"):
        if( float(sensorData["/Temperature"]) < thresholds['temperatureMax']):
                images[0] = inRangeImages[0]            
            else:
                images[0] = outsideRangeImages[0]
   ~~~
3. Show the effect of light by checking the luminance from the sensor data.
    ~~~python
    if (topic == "/Lux"):
            if( float(sensorData["/Lux"]) < thresholds['luminanceMax']):
                images[1] = inRangeImages[1]
            else :
                images[1] = outsideRangeImages[1]
    ~~~
4. Show effect of humidity by checking the humidity from the sensor data.
    ~~~python
    if (topic == "/Humidity"):
            if(float(sensorData["/Humidity"]) > thresholds['humidityMax']):
                images[2] = outsideRangeImages[2]
            else:
                images[2] = inRangeImages[2]
   


        sensorData["images"] =images
    ~~~




* Save and run the code to check the output.
