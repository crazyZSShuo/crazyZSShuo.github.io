#### Running docker container : iptables: No chain/target/match by that name

1. Clear all chains:

sudo iptables -t filter -F

sudo iptables -t filter -X


2. Then restart Docker Service:

systemctl restart docker
