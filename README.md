# Raspberry Pi Internet Speed Monitor

![Speedtest_dashboard](https://user-images.githubusercontent.com/5100075/120923789-9b1d2900-c68d-11eb-9c85-1fc56b2c77de.png)

Grafana, InfluxDB and a Speedtest.net CLI test<br>
Used PimpMyLife setup here - https://pimylifeup.com/raspberry-pi-internet-speed-monitor/<br>
I am not using the uplink to GDrive.<br>

Plans for this project was to evaluate the quality of service of my ISP (T-Mobile Home Internet), with periodical tests along the day.<br>

WARNING!!! The config file that I used executes a speedtest test every 10 minutes, this will use a massave amount of data so if you have a metered connection I suggest bumping it to 1 hour or more.<br>

How you can set up your Raspberry Pi to monitor your internet connection and save the data to view in Grafana.<br>
If you’re interested in monitoring how your download speed, upload speed, and ping are affected over time.<br>
Additionally, this can help you work out what times your network may be at its peak capacity or if you’re suffering from a degraded internet connection.<br>
It's a small Python script that interacts with a program called Speedtest CLI from Ookla.<br>
Speedtest CLI is what our internet speed monitor will use to monitor the internet connection.<br>
This program works by polling the popular speedtest.net service to get your ping, download speed, and upload speed.<br>


IMPORTANT NOTE: If you use this, it will download a decently-large amount of data through your Internet connection on a daily basis. Don't use it, or tune the internet-monitoring setup to not run the speedtests as often, if you have a metered connection!<br>
