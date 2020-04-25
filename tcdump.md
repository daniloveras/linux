

# 
tcpdump -i ens160 'tcp[13] & 4 != 0'

tcpdump -n -v 'tcp [tcpflags] & (tcp-rst)! = 0'
