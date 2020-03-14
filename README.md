# nmap
# --
前期交互阶段
情报收集阶段
威胁建模阶段
漏洞分析阶段
渗透攻击阶段
后渗透测试阶段
渗透测试报告


gfw长城防火墙
facebook，youtube

翻墙：
http代理，socks代理，ssh代理，vpn

goagent

tor


zenmap是一个开放源代码的网络探测和安全审核的工具，它是nmap安全扫描工具的图形界面前端，它可以支持跨平台。使用ze
nmap工具可以快速地扫描大型网络或单个主机的信息。如扫描主机提供了哪些服务，使用的操作系统等。

Nmap（“网络映射器”）是免费开放源代码（许可证）实用程序，用于网络发现和安全审核。许多系统和网络管理员还发现它对于
诸如网络清单，管理服务升级计划以及监视主机或服务正常运行时间之类的任务很有用。Nmap以新颖的方式使用原始IP数据包来确定网
络上可用的主机，这些主机提供的服务（应用程序名称和版本），它们正在运行的操作系统（和OS版本），包过滤器/防火墙的类型。正在
使用中，还有许多其他特性。它旨在快速扫描大型网络，但可以在单个主机上正常运行。Nmap可在所有主要的计算机操作系统上运行，并且
官方二进制程序包可用于Linux，Windows和Mac OSX。除了经典的命令行Nmap可执行文件之外，Zenmap），灵活的数据传输，重定向和调试工
具（Ncat），用于比较扫描结果的实用程序（Ndiff）以及数据包生成和响应分析工具（Nping）。

在执行Nmap时，所有的键盘敲击都被记录。这使得用户可以与 程序交互而不需要终止或重启。特定的键可改变选项，其它键会输出 一个有
关扫描的状态消息。约定如下，小写字母增加 打印量，大写字母减少打印量。
v / V
增加 / 减少细节

d / D
提高 / 降低调试级别

p / P
打开/ 养老报文跟踪

nmap -A -T4 scanme.nmap.org
唯一Nmap参数是-A，以启用操作系统和版本检测，脚本扫描和traceroute；-T4为了更快的执行；然后是主机名


nmap -v scanme.nmap.org
这个选项扫描主机scanme.nmap.org中 所有的保留TCP端口。选项-v启用细节模式。


nmap -sS -O scanme.nmap.org/24
进行秘密SYN扫描，对象为主机Saznme所在的“C类”网段 的255台主机。
同时尝试确定每台工作主机的操作系统类型。因为进行SYN扫描 和操作系统检测，这个扫描需要有根权限。


nmap -sV -p 22，53，110，143，4564 198.116.0-255.1-127
进行主机列举和TCP扫描，对象为B类188.116网段中255个8位子网。这 个测试用于确定系统是否运行了sshd、DNS、imapd或4564端口。如果这些端
口 打开，将使用版本检测来确定哪种应用在运行。


nmap -v -iR 100000 -P0 -p 80
随机选择100000台主机扫描是否运行Web服务器(80端口)。由起始阶段 发送探测报文来确定主机是否工作非常浪费时间，而且
只需探测主机的一个端口，因 此使用-P0禁止对主机列表。

nmap -P0 -p80 -oX logs/pb-port80scan.xml -oG logs/pb-port80scan.gnmap 216.163.128.20/20
扫描4096个IP地址，查找Web服务器(不ping)，将结果以Grep和XML格式保存。

host -l company.com | cut -d -f 4 | nmap -v -iL -
进行DNS区域传输，以发现company.com中的主机，然后将IP地址
提供给 Nmap。上述命令用于GNU/Linux -- 其它系统进行区域传输时有不同的命令。
