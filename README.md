# Raspberry Pi Internet Speed Monitor

![Speedtest_dashboard](https://user-images.githubusercontent.com/5100075/120923789-9b1d2900-c68d-11eb-9c85-1fc56b2c77de.png)

# Grafana, InfluxDB and a Speedtest.net CLI test<br>
Used PimpMyLife setup here - https://pimylifeup.com/raspberry-pi-internet-speed-monitor/<br>
If you didn't use the above link, make sure you setup InfluxDB's database NAME, LOGIN, and PASSWAORD when entering the data into Grafana.<br>
I'm also not using the uplink to GDrive.<br>

# Plans for this project was to evaluate the quality of service of my ISP (T-Mobile Home Internet).<br>

How you can set up your Raspberry Pi to monitor your internet connection and save the data to view in Grafana.<br>
If you’re interested in monitoring how your download speed, upload speed, and ping are affected over time.<br>
Additionally, this can help you work out what times your network may be at its peak capacity or if you’re suffering from a degraded internet connection.<br>
It's a small Python script that interacts with a program called Speedtest CLI from Ookla.<br>
Speedtest CLI is what our internet speed monitor will use to monitor the internet connection.<br>
This program works by polling the popular speedtest.net service to get your ping, download speed, and upload speed.<br>

# Servers<br>
Running the following command to list the servers that are located near you.<br>

<code>speedtest -L</code>

Make a note of the ID for the server you want try connecting to.<br>
Once you have an ID handy. Modify the following line in the Python script.<br>
Find:<br>

<code>response = subprocess.Popen('/usr/bin/speedtest --accept-license', shell=True, stdout=subprocess.PIPE).stdout.read().decode('utf-8')</code><br>

Replace:<br>

<code>'/usr/bin/speedtest --accept-license'</code><br>

With:

<code>'/usr/bin/speedtest --accept-license -s SERVERID'</code><br>

Make sure that you replace SERVERID with the ID you retrieved from the previous list.<br>

# Updating Speedtest:<br>
You should be able to update the speedtest-cli python package by running the following command.<br>

<code>pip install speedtest-cli --upgrade</code><br>

IMPORTANT NOTE: If you use this, it will download a decently-large amount of data through your Internet connection on a daily basis. Don't use it, or tune the internet-monitoring setup to not run the speedtests as often, if you have a metered connection!<br>

# Automating your Speed Monitor script with Grafana<br>

The easiest way to automate your script to run every so often is to make use of the crontab.<br>
You can modify the crontab by running the following command on your Raspberry Pi.<br>

<code>crontab -e</code><br>

This cronjob will run every 30 minutes.<br>

<code>*/30 * * * * python3 /home/pi/speedtest.py</code><br>

Thanks to PimpMyLife!

