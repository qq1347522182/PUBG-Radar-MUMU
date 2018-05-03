

# MUMU 兰海科技地图雷达
这个版本CPU占用率比较大，不建议使用移动设备访问。这可能会造成发热严重的情况。

# 方法:第一步_搭建SS
在服务器的控制面板中，依次输入以下命令
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
执行完这行代码后会让你选择，你是选择搭建单独SS还是SSR 更具自己需求 默认是第一个SS
之后会让你设置一个连接SS的密码
然后会让你选择一个端口(1~65535)非占用端口，随意设置
最后是让你选择加密协议 直接按回车默认aes-256-gcm即可
选择玩之后会提示你按任意键开始或按Ctrl+C取消，这里直接按回车开始搭建
搭建完成后会出现服务器IP 设置好的 端口号 密码 加密方式等. 这样就表示你的SS服务器搭建完成了

# 方法:第二步_安装Nodejs npm
在服务器的控制面板中，依次输入以下命令
curl https://raw.githubusercontent.com/creationix/nvm/v0.13.1/install.sh | bash
source ~/.bash_profile
nvm install v9.8.0
nvm alias default v9.8.0

# 方法:第三步_安装libpcap
在服务器的控制面板中，依次输入以下命令
yum -y install gcc-c++
yum -y install flex
yum -y install bison
wget http://www.tcpdump.org/release/libpcap-1.8.1.tar.gz
tar -zxvf libpcap-1.8.1.tar.gz
cd libpcap-1.8.1
./configure
make
make install

# 方法:第四步_安装雷达
在服务器的控制面板中，依次输入以下命令
yum install git
git clone https://github.com/qq1347522182/PUBG-Radar-MUMU.git
cd PUBG-Radar-MUMU/
npm i
npm i -g pino
npm install -g forever
forever start index.js sniff eth0 XX.XX.XX.XX | pino
(此处的XX填写 你购买的服务器的内网IP )

# 使用
打开SSTap 或其他工具，连接到你刚搭建好的SS
打开浏览器输入你服务器的外网IP+20086 如:0.0.0.0:20086
运行游戏即可


