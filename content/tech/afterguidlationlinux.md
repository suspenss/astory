+++
 title = "some linux configurations" 
 date = "2022-11-02T21:49:46+08:00" 
 tags = ["linux"] 
 slug = "linuxnote1"
 description = ""
 # indent = true
+++
### some configruations on linux

这些天把  Arch linux 装回来了, `gnome 43`，英伟达闭源驱动加`wayland`，和这台破机器运行的 win11 相比，linux 要流畅太多了，装机不易，耗时耗力，然而谁有没有做过无聊的事情呢? 有时候我们只是需要暂时脱离宏大叙事，感受一下个人的悲欢而已，所以写文章要先撇清和 all kinds of ism 的关系。


##### grub and touble system
使用 grub 引导双系统 win11 和 arch linux， 需要安装 os-prober。                
编辑 `/etc/default/grub`。
```
# /etc/default/grub
# 找到下方内容并取消注释
GRUB_DISABLE_OS_PROBER=false
```
然后生成 grub 配置文件
```
grub-mkconfig -o /boot/grub/grub.cfg
```
在 live CD 中 chroot 进入 arch 的条件下有检测不到 win boot manager 的机率，无论是否挂载了 win efi 的分区，在遇到这种情况的时候重启再操作一遍就可以了。

##### wayland plus nvidia close source driver
这台破机器在 x11 的 gnome 下打字延迟很严重，所以切换到了 wayland，为了性能也需要安装 nvidia 闭源驱动，所以列出在这种情况下开启 wayland 的方法。

检查 nvidia 驱动版本是否大于 R490 

```
# Add the kernel parameter 
# /etc/default/grub
# 在 GRUB_CMDLINE_LINUX_DEFAULT=" " 里添加如下内容
nvidia-drm.modeset=1
```

重启查看 gnome 设置关于界面，如果还是 x11 那么直接执行下面命令屏蔽 udev 检测。
```
sudo ln -s /dev/null /etc/udev/rules.d/61-gdm.rules
```


##### paru, a aur helper
请编译安装。
##### helix, a post-morden editor
在 archlinux 官方源里面已经有打包好的安装包，直接用包管理器安装即可，不用编译所有的语法树，但是命令会从 hx 变为 helix。
```
whereis helix
```
找到 helix 二进制文件的路径，重命名即可。
