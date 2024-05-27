cd
apt-get install curl nodejs npm
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
git clone https://github.com/CiscoDevNet/OpenDaylight-OpenFlow-App.git
sed -i 's/localhost/192.168.2.10/g' ./OpenDaylight-OpenFlow-App/ofm/src/common/config/env.module.js
npm install -g grunt-cli

cd distribution-karaf-0.3.0-Lithium.tar.gz
./bin/karaf

OTRA TERMINAL
cd OpenDaylight-OpenFlow-App
grunt
