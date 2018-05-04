mtk3339
=======

Python library for Raspberry PI for Ultimate GPS based on MTK3339 with serial interface as sold by Adafruit. The library helps to set different chip parameters in a sane way. Currently supports minimum functional set of commands:

-	`CMD_HOT_START` - `hot_start()`
-	`CMD_WARM_START` - `warm_start()`
-	`CMD_COLD_START` - `cold_start()`
-	`CMD_FULL_COLD_START` - `cold_reset()`
-	`SET_NMEA_UPDATERATE` - `set_nmea_update_rate()`
-	`SET_NMEA_BAUDRATE` - `set_baudrate()`
-	`API_SET_FIX_CTL` - `set_fix_update_rate()`
-	`API_SET_NMEA_OUTPUT` - `set_nmea_output()`
-	`SET_NAV_SPEED_TRESHOLD` - `set_nav_speed_threshold()`

All functions are preforming basic range check to make sure values are accepted by MTK3339 as there is no check if a call was successful or not.

Example usage:

```
import mkt3339
gps = mt3339("/dev/ttyAMA0")
gps.set_fix_update_rate(800)
gps.set_nmea_update_rate(800)
gps.set_baudrate(115200)
gps.set_nmea_update_rate(1000)
gps.set_nav_speed_threshold(1.5)
gps.set_nmea_output(gll = 0, rmc = 1, vtg = 0, gga = 5, gsa = 5, gsv = 5)
```

Update
------

This fork is compatible with **Python 3.5.1** and tests on **Phytec MIRA Board**

ChangeLog
---------

-	use `functools` to use `reduce`
-	replace `encode` with `str`
-	use `str.encode()` to send information on `serial.write`
