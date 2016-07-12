# ubuntu命令

**端口转发**

iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3001

**端口转发查看**
iptables --line-numbers --list PREROUTING -t nat

