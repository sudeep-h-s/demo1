# demo1

#!/bin/bash
cd ../
echo Stoping Batch Module....
appHome=`pwd`
pid=$(ps -Aef|grep `pwd`|grep -v grep |awk '{print $2}')
kill -9 $pid
echo Removing nohup.out file.....
if [ -f bin/nohup.out ]
then
rm -rf bin/nohup.out
fi
cd standalone/log/
timeNow=`(date --date='now' '+%Y-%m-%d_%H')`
cd ${appHome}/bin
echo Restarting Apllication.....
nohup  ./standalone.sh -bmanagement=127.0.0.1 -b 0.0.0.0 &
sleep 5
