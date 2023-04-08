**English** | [中文](https://p3terx.com/archives/build-openwrt-with-github-actions.html)

# Actions-OpenWrt

2022年11月25日，根据视频踩了坑，排了坑编译成功的过来，总结如下：
1、教程第二种ssh配置固件进行编译的时候，每隔30分钟不移动键鼠的话，编译就被GitHub自动停止，而且编译固件时间长达3个小时左右。
2、第一种方法编译固件目前可行，不需要人员值守，可以关机离开，编译一般不会中断。但是配置文件 .config的名字不是随便写的，只能是.config，不然编译固件时候不写入自定义配置。
3、写给不想用网上的.config配置文件，喜欢自定义.config配置文件的朋友：
（1）Fork P3TERX的编译脚本到自己的仓库，最开始使用第二种ssh编译的方法，进入ssh界面，执行cd openwrt && make menuconfig   选好要编译的插件，保存后不要退出ssh，执行make defconfig   再执行./scripts/diffconfig.sh
（2）ssh界面会弹出自定义的那部分配置项，从配置项设备选项开始一直复制到配置项的最后一行，保存到本地记事本上。快捷键ctrl+D或者输入ssh里输入exit并回车，就可以退出ssh。再取消并删除这个编译流程。
（3）回到自己的编译脚本仓库code页面，用视频的第一种编译方法，创建.config文件，把seed.config里的代码粘贴进去，提交.config代码，然后用视频里的第一种编译方法就可以编译自己需要的固件。

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

A template for building OpenWrt with GitHub Actions

## Usage

- Click the [Use this template](https://github.com/P3TERX/Actions-OpenWrt/generate) button to create a new repository.
- Generate `.config` files using [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) source code. ( You can change it through environment variables in the workflow file. )
- Push `.config` file to the GitHub repository.
- Select `Build OpenWrt` on the Actions page.
- Click the `Run workflow` button.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

## Tips

- It may take a long time to create a `.config` file and build the OpenWrt firmware. Thus, before create repository to build your own firmware, you may check out if others have already built it which meet your needs by simply [search `Actions-Openwrt` in GitHub](https://github.com/search?q=Actions-openwrt).
- Add some meta info of your built firmware (such as firmware architecture and installed packages) to your repository introduction, this will save others' time.

## Credits

- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub Actions](https://github.com/features/actions)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [ActionsRML/delete-workflow-runs](https://github.com/ActionsRML/delete-workflow-runs)
- [dev-drprasad/delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
- [peter-evans/repository-dispatch](https://github.com/peter-evans/repository-dispatch)

## License

[MIT](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © [**P3TERX**](https://p3terx.com)
