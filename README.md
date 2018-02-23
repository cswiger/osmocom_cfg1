# osmocom_cfg1
My working single computer working Osmocom cfg files for nitb and gprs

These are the osmocom .cfg files that work for my setting up an osmo-nitb 2G cell with GPRS.
Largely following https://osmocom.org/projects/cellular-infrastructure/wiki/OpenBSC_GPRS
with hints from videos: https://www.youtube.com/watch?v=2SNb4pXnN80&app=desktop
and: https://www.youtube.com/watch?v=Y5Jww5BWRx4&app=desktop

These are all run on a single PC - Dell OptiPlex with Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz running Ubuntu 16.04
with ufw disabled, iptables -F; iptables -t nat -F; and
  iptables -A POSTROUTING -t nat -o eno1 -j MASQUERADE      <-- change to your nic interface 
with ip_forward 1 in /proc/sys/net/ipv4/ip_forward

Run in screen sessions in the directory with the .cfg files, and using USB3 to a LimeSDR radio board.
I'm also using 10MHz clock reference from a Trimble Thunderbolt and extREF set.

Startup, in each terminal or screen:
# osmo-trx -b 4 -s 4
# osmo-nitb -m -P
# lcr start
# osmo-pcu
# osmo-sgsn
# osmo-ggsn
# osmo-bts-trx
