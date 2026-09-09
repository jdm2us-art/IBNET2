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


