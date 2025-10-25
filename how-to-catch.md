机顶盒接openwrt路由器，路由器安装好tcpdump，路由器接光猫，电脑连接路由器WiFi
启动wireshark→ssh remote齿轮→用户名密码→capture-remote旷填入br-lan（根据路由器lan接口名字决定）→开始
机顶盒通电，抓取1-2分钟
停止抓取，Ctrl+F查找字符串：channel
所在条目右键→追踪流→http……，搜索东方卫视（比如），确定抓取到列表，然后数据另存为
用editplus软件进行处理，去除头尾不需要的数据，然后正则表示替换即可

正则表达式一下几项，全部替换为空的项目
            <script>\n
            </script>\n
            var iRet;\n
#如果生成播放列表，“            var iRet;\n”替换为“#EXTINF:-1,”
查找“^.*ChannelName="(.*)",UserChannelID="(.*)",.*(igmp.*)",TimeShiftURL="(.*)",ChannelType=.*”替换为“\1,\4\n”，如果生成播放列表，改为“\1\n\4\n”

^.*ChannelName="(.*)",UserChannelID="(.*)",.*(igmp.*)",TimeShiftURL="(.*)",ChannelType=.*
\1,\4\n

去除多余的回车：将"\n\n"（两个连续的换行符）替换为"\n"

\n\n
\n

记得手动去除最后一行的</script>
2025.10.25修正下错别字
