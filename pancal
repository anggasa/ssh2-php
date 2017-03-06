# install wget and curl
apt-get update;apt-get -y install wget curl;

# set time GMT +7
ln -fs /usr/share/zoneinfo/Asia/Jakarta /etc/localtime

cd
wget 'https://raw.githubusercontent.com/anggasa/worm/master/screenfetch-dev'
mv screenfetch-dev /usr/bin/screenfetch-dev
chmod +x /usr/bin/screenfetch-dev
echo "clear" >> .profile
echo "screenfetch-dev" >> .profile

 # install webserver
apt-get install apache2 php5 -y
apt-get install libssh2-php

# install dropbear
apt-get -y install dropbear
sed -i 's/NO_START=1/NO_START=0/g' /etc/default/dropbear
sed -i 's/DROPBEAR_PORT=22/DROPBEAR_PORT=443/g' /etc/default/dropbear
sed -i 's/DROPBEAR_EXTRA_ARGS=/DROPBEAR_EXTRA_ARGS="-p 443 -p 110 -p 2017"/g' /etc/default/dropbear
echo "/bin/false" >> /etc/shells
echo "/usr/sbin/nologin" >> /etc/shells
service ssh restart
service dropbear restart

# upgrade dropbear 2014
apt-get install zlib1g-dev
wget https://raw.githubusercontent.com/anggasa/worm/master/dropbear-2014.63.tar.bz2
bzip2 -cd dropbear-2014.63.tar.bz2  | tar xvf -
cd dropbear-2014.63
./configure
make && make install
mv /usr/sbin/dropbear /usr/sbin/dropbear1
ln /usr/local/sbin/dropbear /usr/sbin/dropbear
service dropbear restart

cd
wget -O create-user.sh "https://raw.githubusercontent.com/anggasa/worm/master/create-user.sh"
wget -O speedtest_cli.py "https://raw.githubusercontent.com/anggasa/worm/master/speedtest_cli.py"
wget -O bench-network.sh "https://raw.githubusercontent.com/anggasa/worm/master/bench-network.sh"
wget -O ps_mem.py "https://raw.githubusercontent.com/anggasa/worm/master/ps_mem.py"
wget -O dropmon "https://raw.githubusercontent.com/anggasa/worm/master/dropmon.sh"
wget -O user-login.sh "https://raw.githubusercontent.com/anggasa/worm/master/user-login.sh"
wget -O user-expired.sh "https://raw.githubusercontent.com/anggasa/worm/master/user-expired.sh"
#wget -O userlimit.sh "https://raw.githubusercontent.com/anggasa/worm/master/limit.sh"
wget -O user-list.sh "https://raw.githubusercontent.com/anggasa/worm/master/user-list.sh"
wget -O /etc/issue.net "https://raw.githubusercontent.com/anggasa/worm/master/banner"
echo "0 0 * * * root /root/user-expired.sh" > /etc/cron.d/user-expired
#echo "@reboot root /root/userlimit.sh" > /etc/cron.d/userlimit
echo "0 0 * * * root /usr/bin/reboot" > /etc/cron.d/reboot
echo "* * * * * service dropbear restart" > /etc/cron.d/dropbear
#sed -i '$ i\screen -AmdS check /root/autokill.sh' /etc/rc.local
chmod +x bench-network.sh
chmod +x speedtest_cli.py
chmod +x ps_mem.py
#chmod +x user-login.sh
chmod +x user-login.sh
#chmod +x user-expired.sh
chmod +x user-expired.sh
#chmod +x userlimit.sh
chmod +x dropmon
chmod +x user-list.sh
#chmod +x create-user.sh
cp /root/create-user.sh /usr/bin/usernew
chmod +x /usr/bin/usernew
#chmod +x trial.sh
cd /usr/bin
curl https://raw.githubusercontent.com/anggasa/worm/master/trial.sh > trial
chmod +x trial
cd
