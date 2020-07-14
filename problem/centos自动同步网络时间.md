1. 使用`yum install ntpdate`安装这个工具
2. 然后使用`ntpdate -u ntp.sjtu.edu.cn`从该服务器同步系统时间
3. 再将硬件时间设置为系统时间`hwclock -w`

4. 如有必要，可以设置定时任务执行自动更新时间执行`crontab -e`，编辑`* 0,12 * * * ntpdate -u ntp.sjtu.edu.cn&&hwclock -w     #更新系统时间`这样每12小时会进行时间同步更新。