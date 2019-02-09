### Set brightness
```echo 300 > /sys/class/backlight/intel_backlight/brightness```

Replace ```intel_backlight``` with appropriate controller name.

### Script to set brightness
```bash
#!/bin/bash
if [ $# != 1 ]
then
	echo 'Usage: bt.sh [brightness_number]'
	exit
fi
echo $1 | tee -a /sys/class/backlight/intel_backlight/brightness >/dev/null
```
