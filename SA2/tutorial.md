Set the Threshold
======================
In this activity, you will set the threshold for the sensor data using form.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/11130882/pasted-from-clipboard.png" width = "100%" height = "50%">




Follow the given steps to complete this activity.




1. Create a function to set the threshold by creating a route to the function for POST requests.
   ~~~python
    @app.route('/setThresholds', methods=['POST'])
    def set_thresholds():
        global thresholds
   ~~~
2. Get the values form the form by accessing the data from the form if the method is POST.
   
   ~~~python
    if request.method == 'POST':
        temperatureMin = request.form.get('temperatureMin')
        temperatureMax = request.form.get('temperatureMax')


        humidityMin = request.form.get('humidityMin')
        humidityMax = request.form.get('humidityMax')


        luminanceMin = request.form.get('luminanceMin')
        luminanceMax = request.form.get('luminanceMax')


        gforceMin = request.form.get('gforceMin')
        gforceMax = request.form.get('gforceMax')
   ~~~
3. Update the threshold values by storing the values in the global variable `thresholds`.
    ~~~python
    thresholds = {
                'temperatureMin': temperatureMin,
                'temperatureMax': temperatureMax,
                'humidityMin': humidityMin,
                'humidityMax': humidityMax,
                'luminanceMin': luminanceMin,
                'luminanceMax': luminanceMax,
                'gforceMin': gforceMin,
                'gforceMax': gforceMax
            }
    ~~~
4. Navigate to the home page by redirecting to the root url.
    ~~~python
    return redirect("/")
    ~~~




* Save and run the code to check the output.
