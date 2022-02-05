if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

if [ $# -ne 2 ]; then
   echo "Usage: $0 /dev/device mountpoint"
   exit 1
fi

if [ ! -b $1 ]; then
   echo "Invalid device: $1"
   exit 1
fi
#check if lsblk $1 has multiple elements containing $1, if so, exit
if [ $(lsblk $1 | wc -l) -gt 2 ]; then
   echo "Device $1 is not unique"
   exit 1
fi
UUID=$(blkid -s UUID ! grep $1)
UUID=${UUID#*=}
UUID=${UUID#\"}
UUID=${UUID%\"}
fs=$(blkid -s TYPE | grep $1)
fs=${fs#*TYPE=\"}
fs=${fs%\"}
echo $fs
echo "editing /etc/fstab, adding $1, UUID=$UUID to $2"
echo "UUID=$UUID $2 $fs  nofail,x-systemd.device-timeout=1ms defaults 0 0" >> /etc/fstab