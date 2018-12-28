# subnetter
bash script to subdivide a given CIDR /24 and smaller subnets into a pre-defined number of smaller subnets

After division IP addresses shouldn't be wasted, i.e. accumulation of your subdivisions should make up
the divided subnet.
Every subnet has 3 IP addresses reserved and not usable by hosts: network, broadcast, gateway.
Show network/broadcast address, number of hosts and assign gateway. Gateway should be first IP
available in divided subnet.
Considerations:
(1) Tough this script makes sure that the division happens with minimum wastage of hosts. So, if it
is not possible to further subdivide, it keeps all the remaining hosts into the last group.
(2) Making such last group as above, it might be possible that the number of groups actually made
by the script are less than the ones asked to be formed in arguments ($2).
(3) Similarly, if maximum possible hosts (say 256 in case of /24) are already formed, the script gives
up further subgrouping. In this case too, it might be possible that the number of groups actually
made by the script are less than the ones asked to be formed in arguments ($2).
(4) Output is a little different from the example given. Smaller grouping is printed first and then the
larger grouping. However, logically, the group strength and host utilization is same.
Test Cases ran:
This script is tested extensively on CIDR IP scheme upto 9 subgroups.
Almost every corner case has been handled.
Below are the test cases ran:
(1) ./subnetter.sh 192.168.0.0/24 2
(2) ./subnetter.sh 192.168.0.0/24 3
Have a look at the output here. This is the case of Consideration No. 4 which says output
sequence is different from the given example. But the logical division of subnet is same.
(3) ./subnetter.sh 192.168.0.0/24 4
(4) ./subnetter.sh 192.168.0.0/24 5
(5) ./subnetter.sh 192.168.0.0/24 6
Have a look at the WARNING here. This is the case of Consideration No. 3.
(6) ./subnetter.sh 192.168.0.0/24 7
(7) ./subnetter.sh 192.168.0.0/24 8
Have a look at the WARNING here. This is the case of Consideration No. 1-2.
(8) ./subnetter.sh 192.168.0.0/24 9
