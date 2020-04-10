# Actions-OpenWrt

本库Fork自

<https://github.com/P3TERX/Actions-OpenWrt>

相关的使用，请参考[原作者的博客](https://p3terx.com/archives/build-openwrt-with-github-actions.html)


## 补充

如下根据自身的使用场景， 基于[原作者博客](https://p3terx.com/archives/build-openwrt-with-github-actions.html)内容的基础上，做的一点补充

### 如何生成`.config`

### 方法一

直接在`.github/workflows/build-openwrt.yml`开启ssh登录，然后ssh到服务端执行`make menuconfig`进行定制

### 方法二

直接使用别人配置好的

<https://github.com/esirplayground/AutoBuild-OpenWrt>

### 方法三

自己搭建编译环境生成，参考下面的[链接](https://github.com/coolsnowwolf/lede)搭建本地编译环境,然后执行

```bash
$ make menuconfig
```

选择要安装的软件包和定制的配置项

```bash
$ ./scripts/diffconfig.sh > diffconfig # write the changes to diffconfig
$ cp diffconfig .config   # write changes to .config
$ make defconfig   # expand to full config
```

编译步骤定制可以参考:

 <https://openwrt.org/docs/guide-developer/build-system/use-buildsystem>

## 把自己编译的固件打包成Docker镜像

请参考:

<https://github.com/crazygit/openwrt-x86-64>
