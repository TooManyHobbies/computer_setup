#!/bin/bash



printf '#!/bin/bash\n' > /usr/sbin/writeintelbacklight.sh
printf '\n' >> /usr/sbin/writeintelbacklight.sh
printf 'intelmaxbrightness=`cat /sys/class/backlight/intel_backlight/max_brightness`\n' >> /usr/sbin/writeintelbacklight.sh
printf 'acpimaxbrightness=`cat /sys/class/backlight/acpi_video0/max_brightness`\n' >> /usr/sbin/writeintelbacklight.sh
printf 'scale=`expr $intelmaxbrightness / $acpimaxbrightness`\n' >> /usr/sbin/writeintelbacklight.sh
printf 'acpibrightness=`cat /sys/class/backlight/acpi_video0/brightness`\n' >> /usr/sbin/writeintelbacklight.sh
printf 'newintelbrightness=`expr $acpibrightness \* $scale`\n' >> /usr/sbin/writeintelbacklight.sh
printf 'curintelbrightness=`cat /sys/class/backlight/intel_backlight/actual_brightness`\n' >> /usr/sbin/writeintelbacklight.sh
printf 'if [ "$newintelbrightness" -ne "$curintelbrightness" ]\n' >> /usr/sbin/writeintelbacklight.sh
printf 'then\n' >> /usr/sbin/writeintelbacklight.sh
printf '  echo $newintelbrightness >> /sys/class/backlight/intel_backlight/brightness\n' >> /usr/sbin/writeintelbacklight.sh
printf 'fi\n' >> /usr/sbin/writeintelbacklight.sh
printf 'exit 0\n' >> /usr/sbin/writeintelbacklight.sh
printf '\n' >> /usr/sbin/writeintelbacklight.sh
chmod +x testfile

printf 'ACTION=="change", SUBSYSTEM=="backlight", RUN+="/usr/sbin/writeintelbacklight.sh"\n' > /etc/udev/rules.d/99-writeintelbacklight.rules
