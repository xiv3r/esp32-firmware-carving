# esp32-firmware-carving
Craved or dump any information from the esp32 firmware.

# Installation 
> linux or termux (ubuntu/debian proot)
```
sudo apt install && sudo apt install binwalk -y
```
- Download any firmware you want to dump the info and execute
```
binwalk --term firmware.bin
```
- Extract all the partitions
```
binwalk --term --dd='.*' firmware.bin --run-as=root
```
- cd to the extracted directory
```
cd _*
```
- Dump extracted data information
```
file * > data.txt
cat data.txt
```
- Select the 0x10000 firmware partitions
```
strings 8040 | grep -i "\.h\|\.cpp"
```
