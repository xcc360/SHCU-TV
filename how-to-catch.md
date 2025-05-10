机顶盒接路由器，路由器接光猫，电脑连接路由器WiFi
启动wireshark→ssh remote齿轮→用户名密码→开始
机顶盒通电，抓取2分钟
停至抓取，查找字符串：channel
所在条目邮件，追踪流，http，数据另存为
用editplus处理，去除头尾部需要的数据，然后正则表示替换即可

正则表达式，替换为空的项目
            <script>\n
            </script>\n
            var iRet;\n
#如果生成播放列表，“            var iRet;\n”替换为“#EXTINF:-1,”
查找^.*ChannelName="(.*)",UserChannelID="(.*)",.*(igmp.*)",TimeShiftURL="(.*)",ChannelType=.*替换为\1,\4\n，如果生成播放列表，改为\1\n\4\n
^.*ChannelName="(.*)",UserChannelID="(.*)",.*(igmp.*)",TimeShiftURL="(.*)",ChannelType=.*
\1,\4\n

去除多余的回车：将"\n\n"（两个连续的换行符）替换为"\n"
\n\n
\n

记得去除最后一行的</script>
