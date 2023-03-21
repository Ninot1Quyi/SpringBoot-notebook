# Watt Toolkit加速github相关问题

1.端口443被占用

1.1问题图例：

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230321100250301.png" alt="image-20230321095939212" style="zoom: 50%;" />

1.2原因：电脑中存在虚拟机，例如VMWare

1.3解决办法：ctrl+shfit+ESC打开任务管理器，选择“详细模式”

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230321100415892.png" alt="image-20230321100250301" style="zoom: 67%;" />



1.4在“后台进程”这一栏中查找进程“vmware-hostd.exe (32位)”

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230321100521029.png" alt="image-20230321100415892" style="zoom:50%;" />

1.5右键，结束任务

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230321095939212.png" alt="image-20230321100521029" style="zoom:50%;" />

1.6结束：然后在Watt Toolkit中重新加速即可

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230321100650592.png" alt="image-20230321100650592" style="zoom:50%;" />