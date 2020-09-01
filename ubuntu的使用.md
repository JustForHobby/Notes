# ubuntu的使用



![img](https://csdnimg.cn/release/phoenix/template/new_img/original.png)



## 1安装windows字体

例如安装宋体

第一步，从网上下载或从C:\WINDOWS\Fonts 中拷贝一个字体

宋体的名字是simsun.ttf



第二步， 在/usr/share/下创建文件夹fonts

在fonts下创建文件夹zh_CN



第三步， 把字体文件拷贝到/usr/share/fonts/zh_CN中





第四步，对这个文件授权，chmod 777 simsun.tff





第五步， 开始安装

在目录/usr/share/fonts/zh_CN下

sudo mkfontscale  (创建字体的fonts.scale文件，控制字体的选装缩放)

sudo mkfontdir  (创建字体的fonts.dir文件，控制字体粗斜体产生)

sudo fc-cache -fv  (建立字体缓存信息，也就是让系统认识这个字体--即安装)





注：无需重启



删除字体

找到/usr/share/ 删掉fonts文件夹

然后 sudo fc-cache -fv即可