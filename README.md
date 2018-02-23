# osmocom_cfg1
My working single computer working Osmocom cfg files for nitb and gprs

These are the osmocom .cfg files that work for my setting up an osmo-nitb 2G cell with GPRS.<br/>
Largely following https://osmocom.org/projects/cellular-infrastructure/wiki/OpenBSC_GPRS<br/>
with hints from videos: https://www.youtube.com/watch?v=2SNb4pXnN80&app=desktop<br/>
and: https://www.youtube.com/watch?v=Y5Jww5BWRx4&app=desktop<br/>

These are all run on a single PC - Dell OptiPlex with Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz running Ubuntu 16.04<br/>
with ufw disabled, iptables -F; iptables -t nat -F; and<br/>
  iptables -A POSTROUTING -t nat -o eno1 -j MASQUERADE      <-- change to your nic interface <br/>
with ip_forward 1 in /proc/sys/net/ipv4/ip_forward<br/>

Run in screen sessions in the directory with the .cfg files, and using USB3 to a LimeSDR radio board.<br/>
I'm also using 10MHz clock reference from a Trimble Thunderbolt and extREF set.<br/>

Startup, in each terminal or screen:<br/>
 \# osmo-trx -b4 -s4            LimeSDR needs settings for TX/RX Samples-per-symbol<br/>
 \# osmo-nitb -m -P<br/>
 \# lcr start<br/>
 \# osmo-pcu<br/>
 \# osmo-sgsn<br/>
 \# osmo-ggsn<br/>
 \# osmo-bts-trx<br/>
