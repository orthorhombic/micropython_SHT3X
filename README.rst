
Introduction
============

Micropython  module for the SHT3X series (SHT30-D, SHT31-D, and SHT35-D) temperature and humidity sensors.

Dependencies
=============
This driver depends on:

machine.i2c


Usage Example
=============
You must import the library to use it:

.. code:: python

    import adafruit_sht31d

This driver takes an instantiated and active I2C object as an argument to its constructor.  The way to create
an I2C object depends on the board you are using.

Once you have created the I2C interface object, you can use it to instantiate
the sensor object:

.. code:: python

    sensor = adafruit_sht31d.SHT31D(i2c)


And then you can start measuring the temperature and humidity:

.. code:: python

    print(sensor.temperature)
    print(sensor.relative_humidity)

You can instruct the sensor to periodically measure the temperature and
humidity, storing the result in its internal cache:

.. code:: python

    sensor.mode = adafruit_sht31d.MODE_PERIODIC

You can adjust the frequency at which the sensor periodically gathers data to:
0.5, 1, 2, 4 or 10 Hz. The following adjusts the frequency to 2 Hz:

.. code:: python

    sensor.frequency = adafruit_sht31d.FREQUENCY_2

The sensor is capable of storing eight results. The sensor stores these
results in an internal FILO cache. Retrieving these results is simlilar to
taking a measurement. The sensor clears its cache once the stored data is read.
The sensor always returns eight data points. The list of results is backfilled
with the maximum output values of 130.0 ºC and 100.01831417975366 % RH:

.. code:: python

    print(sensor.temperature)
    print(sensor.relative_humidity)

The sensor will continue to collect data at the set interval until it is
returned to single shot data acquisition mode:

.. code:: python

    sensor.mode = adafruit_sht31d.MODE_SINGLE

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_SHT31D/blob/master/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.

Documentation
=============

For information on building library documentation, please check out `this guide <https://learn.adafruit.com/creating-and-sharing-a-circuitpython-library/sharing-our-docs-on-readthedocs#sphinx-5-1>`_.
