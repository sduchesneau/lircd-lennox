# What ?

I succeeded in controlling my Lennox heat pump from a raspberry pi (model B3) and an IR shield (like this one: https://www.amazon.com/dp/B0713SK7RJ/ref=psdc_3230976011_t1_B00K2IICKK)

# Requirements
1. Get a raspberry pi or whatever
2. Get some IR led and receptor gear connected to your GPIO
3. Install lircd on a [d|r]ecent Linux distro like raspbian (follow this guide: https://gist.github.com/prasanthj/c15a5298eb682bde34961c322c95378b)


# How to get the signals from the IR remote:

```sh
sudo service lircd stop # to allow direct access to data with "mode2"
sudo mode2 -m -d /dev/lirc0
```

Copy the numbers that you get in a text file for next step.
One block of number per "complete heat pump configuration" (sent each time you press a key on remote)

# How to create lircd config file:

Copy the header from this file (Great work, @mattjm !): https://github.com/mattjm/Fujitsu_IR/blob/master/lircd.conf
Name the raw command and copy the rows of numbers by carefully starting with "4 tabs" and single-spacing the entries and ending with a single space...


# How to control the heat pump

Send commands like these:
```
irsend send_once lennox off
irsend send_once lennox heat-17

```

