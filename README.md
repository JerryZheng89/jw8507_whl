# JW8507
![](https://badge.fury.io/py/license.svg)
![LICENSE](https://licensebuttons.net/l/by-nc/4.0/88x31.png)

## JW8507 wheel
This package is the library for device JW8507 or JW8507A
[JW8507 Product Main Page](https://english.joinwit.com/product-info/JW8507A.html)

## Product Overview
JW8507 Multichannel Bench-top Optical Attenuator is a special test equipment designed by Joinwit for current optical transceiver and optical network integration test. JW8506 has a high-density design that significantly small size. The multi-channel stand-alone Optical attenuator channel provides higher test data throughput and test rate. The device also provides variety communication interface, can be integrated with many Joinwit products. JW8507 is the ideal solution of Optical Network, Optical transmission field to light sensitivity, error rate, attenuation test of the 40G / 100G optical module.

## Product Features
1. Individual VOA modules
2. More efficient testing and data processing ability
3. Support for optical output locking
4. Support internal OPM
5. Maximum + 27dBm input optical power
6. Provides RS232 interface
7. Provide variety software protocols for easy system integration

## package install on-line
```shell
pip install jw8507
```

## package install off-line
```shell
# on Macos
pip install jw8507-0.1.2-cp311-cp311-macosx_10_9_universal2.whl

# on Windows
pip install jw8507-0.1.1-cp311-cp311-win_amd64.whl

# on Linux
pip install jw8507-0.1.1-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl

```

## Basic Usage
```python
from jw8507 import JW8507

if __name__ == "__main__":
    jw = JW8507("/dev/cu.PL2303G-USBtoUART2110")
    if jw.open():
        dev_ver = jw.read_device_version()
        print(dev_ver)
        len_list = jw.read_optical_length(1)
        print(len_list)
        len_list = jw.read_optical_length(2)
        print(len_list)
        dev_status = jw.read_current_status(1)
        print(dev_status)
        dev_status = jw.read_current_status(2)
        print(dev_status)

        # set chnnel 1 to 1.1db
        jw.set_attenuation(1100, 1)
        # set chnnel 2 to 1.1db
        jw.set_attenuation(1100, 2)
        time.sleep(5)

        # totally disconnet optical connection
        jw.dis_connection()
        time.sleep(15)


        # restore optical connection, attenattion is 0db
        jw.clear_attenuation(1)
        jw.clear_attenuation(2)
        time.sleep(5)
        # jw.set_attenuation(2200) # set chnnel 1 to 1.1db
        if jw.close_full_screen():
            print("succ close full screen!")
        jw.close()
    else:
        print(f"open serial port:{opat_port} failed!")
```

## How to Support

1. Click the **Star** button in the top right corner to show your support.
2. Share it with others who might be interested to help the project gain more attention.
3. Submit your feedback or issues to help us improve the project.

Thank you for your support! With everyone's participation, we can take this project further!

---

**Note:** Once the Start count is enough, the project will be released as open source, and all the source code will be publicly available on GitHub.
