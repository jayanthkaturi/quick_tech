#### Find out the temperature of the machine
```cat /sys/class/thermal/thermal_zone*/temp```

#### Script to convert to celcius and print (default millidegree celsius)
```bash
#!/bin/bash
TARRAY=$(cat /sys/class/thermal/thermal_zone*/temp)
for TEMP in $TARRAY
do
	echo $(echo $TEMP | awk '{printf "%0.2f*C",$1*0.001}')
done
```
