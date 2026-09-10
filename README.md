# Задание 1.
На картинке изображена схема офисной сети:

Каким образом необходимо настроить все 4 свитча, чтобы в сети корректно работал только один DHCP сервер - маршрутизатор R1. Очень важна корректная конфигурация портов на всех свитчах.

Перечислите список свитчей и список команд, которые необходимо выполнить.

Команды для SW1:

enable  \
configure terminal  \
ip dhcp snooping  \
ip dhcp snooping vlan 1  \
interface gigabitEthernet 0/0  \
 ip dhcp snooping trust  \
 exit  \
interface range gigabitEthernet 0/1 - 47  \
 ip dhcp snooping limit rate 10  \
 ip verify source vlan dhcp-snooping  \
 exit  \
ip dhcp snooping information option allow-untrusted  \
end  \
write memory

Команды для SW2 

enable  \
configure terminal  \
ip dhcp snooping  \
ip dhcp snooping vlan 1  \
interface gigabitEthernet 0/0  \
 ip dhcp snooping trust  \
 exit  \
interface range gigabitEthernet 0/1 - 23  \
 ip dhcp snooping limit rate 10  \
 ip verify source vlan dhcp-snooping  \
 exit  \
ip dhcp snooping information option allow-untrusted  \
end  \
write memory

Команды для SW3

enable  \
configure terminal  \
ip dhcp snooping  \
ip dhcp snooping vlan 1  \
interface gigabitEthernet 0/0  \
 ip dhcp snooping trust  \
 exit  \
interface range gigabitEthernet 0/1 - 23  \
 ip dhcp snooping limit rate 10  \
 ip verify source vlan dhcp-snooping  \
 exit  \
ip dhcp snooping information option allow-untrusted  \
end  \
write memory

Команды для SW4 

enable  \
configure terminal  \
ip dhcp snooping  \
ip dhcp snooping vlan 1  \
interface gigabitEthernet 0/0  \
 ip dhcp snooping trust  \
 exit  \
interface range gigabitEthernet 0/1 - 23  \
 ip dhcp snooping limit rate 10  \
 ip verify source vlan dhcp-snooping  \
 exit  \
ip dhcp snooping information option allow-untrusted  \
end  \
write memory

# Задание 2.

По топологии из задания 1 необходимо на SW2 настроить ARP Inspection и IP Source guard для Client9 и Client10, подключенных к SW2. Client9 получает адрес по DHCP, Client10 ip адрес задан статически. DHCP Snooping уже настроен по первому заданию.

Перечислите список команд, которые необходимо применить на SW2

Команды для SW2:

1. Глобальное включение DAI и настройка VLAN

enable  \
configure terminal  \
ip arp inspection vlan 1  \
ip arp inspection validate src-mac dst-mac ip

2. Настройка доверенных портов для DAI

interface gigabitEthernet 0/0  \
 ip arp inspection trust  \
 exit

3. Настройка порта для Client9 (DHCP)
   
interface gigabitEthernet 0/1  \
 ip verify source vlan dhcp-snooping  \
 ip arp inspection limit rate 15  \
 no ip arp inspection trust  \
 exit

 4. Настройка порта для Client10 (статический IP)

ip source binding 192.168.1.100 aaaa.bbbb.cccc vlan 1 interface gigabitEthernet 0/2

interface gigabitEthernet 0/2  \
 ip verify source vlan dhcp-snooping  \
 ip arp inspection limit rate 15  \
 no ip arp inspection trust  \
 exit
