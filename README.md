About
=====================

RaspberryPi program to control a Super Feeder ( http://super-feed.com/ ) with
easy to program feeding cycles, catch-up feedings in case of power outages, and
the potential for monitoring and logging to make sure the feedings are happening
as expected.

Circuit / Wiring
=====================

For wiring, hook up a ground triggered relay (such as the SainSmart relay modules
( e.g. http://www.sainsmart.com/arduino-pro-mini.html ) to one of the RaspberryPi's pins.

Configuration
=====================

Update the various configuration opions in the Python script to support your particular
feeding schedule, timezone, and GPIO Pin.

Running Automatically
=====================

I installed upstart on my Pi, which allows for a simple configuration script in /etc/init/feeder-control.conf

    description "Cat Feeder - Control / Monitor"
    author "Matthew Bafford <matthew@bafford.us>"
    
    start on runlevel [234]
    stop on runlevel [0156]
    
    console log
    
    chdir /opt/feeder-control/
    exec /opt/feeder-control/feeder_control
    
    respawn

For alternate configurations, just make sure you run the script as root, as the GPIO access needs root.

TODO
=====================

* Move to a different method of GPIO access so that root isn't needed
* Better logging
* Email alerts for missed feedings or catchup feedings
* Webcam monitoring during feedings - perhaps with email alerts with pictures attached
