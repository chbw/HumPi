#HumPi
Using a Raspberry Pi to measure the frequency of the synchronous grid of continental europe

## Hardware requirements
* Raspberry Pi 2
* USB-Soundcard with a microphone or line input
* AC-Power supply with V_out smaller than ~10V.
* [Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider) to
	30mV for microphone input, 1V RMS for line in
* [Phone connector](https://en.wikipedia.org/wiki/Phone_connector_%28audio%29)

Sample circuits can be found within the [HW](https://github.com/gillhofer/HumPi/tree/master/HW) directory. 

## Software requirements
* Python2
* SciPy ([HowTo](http://wyolum.com/numpyscipymatplotlib-on-raspberry-pi/))
* [numexpr](https://github.com/pydata/numexpr), alsaaudio and ntplib. You can install these via pip:
````
    $ pip install -r requirements.txt
````
==========================

### Version 0.5.1

Once started, HumPi captures the signal from an USB-Soundcard and calculates the frequency continuously by fitting a sine on the last second of 'sound'. The frequency of this sine (= the measurment) may be stored to disc using the `--store` parameter or may be sent to [netzsinus](https://github.com/netzsinus) using the `--sendServer` parameter. In case of sending, please also provide an API-Key by specifying the `--apikey` option. If you are annoyed by the console output, there is a `--silent` option.

HumPi requires you to provide a `device` parameter as the first argument, which specifies the ALSA device to use. The parameter can be found by either try and error, or by using the [script](https://github.com/gillhofer/HumPi/blob/master/python/findYourALSADevice.py) within the python directory.

### Install & Run
```
git clone https://github.com/gillhofer/HumPi.git
./HumPi.py 3 --sendServer http://netzsin.us:8080 --apikey secretkey1 --store m.csv --silent True
```

## TODO
* general improvements


