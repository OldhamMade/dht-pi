# DHT11/22 TEMPERATURE & HUMIDITY SENSOR

This repository contains C code and instructions for using UUGear's DHT11 & DHT22
temperature & humidity sensors with the Raspberry Pi. Example taken from [here](http://www.uugear.com/portfolio/read-dht1122-temperature-humidity-sensor-from-raspberry-pi/)

## Usage

Install `git`, clone the `wiringPi` repository:

    $ git clone git://git.drogon.net/wiringPi

...then build & install:

    $ cd wiringPi
    $ ./build

Next, clone this repository:

    $ git clone https://github.com/OldhamMade/dht-pi
    $ cd dht-pi

...and build the binary:

    $ cc -Wall dht.c -o dht -lwiringPi

This binary can be executed with the following command:

    $ sudo ./dht

A `JSON` object will be issued to the console every 2 seconds. Be aware that
reading the data can often fail due to timing issues. In this case, the values
of the `JSON` will all be `null`. It is recommended to cache the last good set
of values to use when `null` values are returned.

For applications, one suggestion for usage would be to move the `dht` binary to
`/usr/local/bin` and run it via a supervisor process (for example,
[supervisord](http://supervisord.org)), capturing the output to a log, then
reading the last line from the log output when needed.
