Receive MQTT Data in Flask
======================
In this activity, you will receive the MQTT data from the broker in flask.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/11130881/1.png" width = "100%" height = "50%">




Follow the given steps to complete this activity.




1. Import `mqtt` library and store the mqtt broker address.
   ~~~python
    import paho.mqtt.publish as publish
    import paho.mqtt.client as mqtt​
    . . .


    mqtt_broker_ip = "broker.emqx.io"
   ~~~
2. Handle `mqtt` messages by creating a function to read and print the sensor data from the mqtt broker.
   
   ~~~python
   def on_message(client, userdata, msg):
    global sensorData
    topic = msg.topic
    payload = msg.payload.decode('utf-8')
    sensorData[topic] = payload
    print(sensorData)
    print("mqtt : ", msg.payload.decode('utf-8') )
   ~~~
3. Setup the mqtt client by creating a constructor and connecting it to the mqtt broker.
    ~~~python
        mqtt_client = mqtt.Client(mqtt.CallbackAPIVersion.VERSION1)
        mqtt_client.on_message = on_message
        mqtt_client.connect(mqtt_broker_ip, 1883, 60)
    ~~~
4. Listen to mqtt messages by subscribing to the four mqtt topics.
    ~~~python
        mqtt_client.subscribe("/Temperature")
        mqtt_client.subscribe("/Humidity")
        mqtt_client.subscribe("/Lux")
        mqtt_client.subscribe("/Gforce")




        mqtt_client.loop_start()
    ~~~


5. Get the sensor data by subscribing to the four mqtt topics.
    ~~~python
    @app.route("/getSensorData", methods=['POST'])
    def getSensorData():
        return jsonify(sensorData)
    ~~~
* Save and run the code to check the output.
