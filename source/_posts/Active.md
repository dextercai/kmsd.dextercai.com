---
title: 激活说明
---

#### 如何选择原版系统镜像

1.微软官方原版系统镜像(MSDN渠道)分两版，business版(即VOL版) 和 consumer版(即RTL版)。

business版镜像名称举例：
zh-cn_windows_11_business_editions_version_22h2_updated_may_2023_x64_dvd_76248ab3.iso

consumer版镜像名称举例：
zh-cn_windows_11_consumer_editions_version_22h2_updated_may_2023_x64_dvd_a95c5a5a.iso

查看镜像名称即可辨别版本。只有使用 business版(即VOL版、批量版、大客户版) 镜像安装的系统才能使用微零微一句命令激活（即KMS激活）。该镜像内包含专业版、企业版、教育版等，安装过程中会有选项。

另外business版安装过程中无输入密钥环节，而consumer版安装过程中会提示输入密钥。

2.微软官方原版系统镜像(VLSC渠道)只提供VOL版，特点是镜像名称以"SW_DVD"开头，例如：

SW_DVD9_Win_Pro_11_22H2_64BIT_ChnSimp_Pro_Ent_EDU_N_MLF_X23-12741.ISO

#### 1.Windows 激活方法

1.打开 命令提示符 (管理员)

开始菜单-搜索“cmd”-找到“命令提示符”-右键“以管理员身份运行”。

2.执行以下命令（复制命令-右键粘贴）

```
slmgr /skms kms.mcdu.xyz && slmgr /ato
```

大部分情况下 你能下载到的系统镜像都是VOL版（Business版）仅需以上一步即可成功激活。

查看系统版本（备用）
wmic os get caption
查看激活详情（备用）
slmgr /dlv
查看所有命令（备用）
slmgr

如果激活失败有两种原因：
a.你无意中修改或卸载了系统自带的KMS激活密钥（比如你曾经使用了MAK密钥或网络上找到的其它密钥尝试激活失败）。
解决办法：命令提示符(管理员)执行以下命令安装对应版本的KMS密钥后重新激活（密钥在文末“附1”）
```
slmgr /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```
b.你安装的系统为RTL版，需要先转换为VOL版才能激活，方法请 [特例]()。
c.更多问题请下拉本文查看“激活失败如何排错”。

#### [特例] Windows11/Windows10 家庭版（RTL版）升级为企业版（VOL版）并激活：

Windows11/10 最新零售版微软官方下载地址：https://www.microsoft.com/zh-cn/software-download/

请使用“手机” 访问，按提示选择版本和语言获取iOS镜像下载链接（电脑直接访问会跳转到更新助手页面）。

该版本安装完默认为 Windows11/10 家庭版（RTL版）依照以下命令升级为企业版（VOL版）并激活。

1.升级。使用 Win+i 快捷键打开「设置」- 点击「更新和安全」- 在左侧点击「激活」选项卡。

点击右侧的「更改产品密钥按钮」- 输入密钥：NPPR9-FWDCX-D2C8J-H872K-2YT43

如果提示密钥错误，请先输入如下密钥升级为专业版后，再输入企业版或者其它版本密钥进行升级。
```
VK7JG-NPHTM-C97JM-9MPGT-3V66T
```

2.激活。按提示升级后打开命令提示符(管理员)逐行执行以下命令：
```
slmgr /ipk NPPR9-FWDCX-D2C8J-H872K-2YT43
slmgr /skms kms.mcdu.xyz && slmgr /ato
```

同样的方法可以升级为专业版、教育版等，以及版本退回切换（政府版不可逆） 。升级密钥在文末“附1”。

全新装机请直接安装VOL版系统，本文末有下载链接。不推荐RTL转VOL的方式装机。

#### 2.Office 激活方法

目前看来 LTSC2021 可能是 Office VOL版的最后一个数字版本，往后只会以 “Microsoft 365 应用企业版” 的形式出现。
微软在 Office 2016 之后不再为VOL版提供ISO镜像(官方离线安装包)。也就是说，以后的VOL版只能使用微软官方 Office部署工具 或者 第三方软件(如：Office Tool Plus) 部署安装。本文末有下载链接。

1.命令提示符(管理员)进入Office OSPP.VBS目录

以 LTSC2021 64位版本为例，默认安装目录是 ``` C:\Program Files\Microsoft Office\Office16 ```
所以，打开命令提示符(管理员)执行以下命令进入OSPP.VBS目录

```
cd C:\Program Files\Microsoft Office\Office16
```

如果你安装的是其它版本 或者 Office安装在其它盘符和路径，参照下文自行修改命令。

Office2016、Office2019、LTSC2021、Office365/Microsoft365 默认安装目录
32位版本：
```
cd C:\Program Files (x86)\Microsoft Office\Office16
```
64位版本：
```
C:\Program Files\Microsoft Office\Office16
```

Office2013 默认安装目录
32位版本：
```
cd C:\Program Files (x86)\Microsoft Office\Office15
```
64位版本：
```
cd C:\Program Files\Microsoft Office\Office15
```

Office2010 默认安装目录
32位版本：
```
cd C:\Program Files (x86)\Microsoft Office\Office14
```
64位版本：
```
cd C:\Program Files\Microsoft Office\Office14
```

总之就是在cmd命令提示符(管理员)内 使用cd命令进入 OSPP.VBS 文件所在的目录。
如果不确定自己安装的Office是32位还是64位，就两行命令都执行一下 不报错的就是对的。

2.执行命令激活Office软件

完成上一步骤后，执行以下命令。
```
cscript ospp.vbs /sethst:kms.mcdu.xyz && cscript ospp.vbs /act
```

大部分情况下 你能下载到的安装包都是VOL版 仅需以上两步即可成功激活。

查询Office激活详情（备用）
```
cscript ospp.vbs /dstatus
```
查看所有命令（备用）
```
cscript ospp.vbs
```

如果激活失败有两种原因：
a.你无意中修改或卸载了Office自带的KMS激活密钥（比如你曾经使用了MAK密钥或网络上找到的其它密钥尝试激活失败）。
解决办法：执行以下命令安装对应版本的KMS密钥后重新激活（密钥在文末“附2”）
```
cscript ospp.vbs /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```
b.你安装的为RTL版Office，需要转换为VOL版才能激活，方法请 [参照特例]()。
c.Mac版的批量版Office不需要KMS激活，只需运行微软提供的 SWDVD5_Office_Mac_Serializer_*.ISO（相当于激活补丁，十几MB）安装即可激活。
d.更多问题请下拉本文查看“激活失败如何排错”。

#### [特例] Office365/Microsoft365 家庭版（RTL版）转换专业版（VOL版）并激活（以64位默认安装目录为例）：

Office365/Microsoft365 最新零售版微软官方下载地址：https://www.microsoft.com/zh-cn/microsoft-365/try

打开链接点击试用1个月按提示下载安装。

该版本安装完默认为 Office365/Microsoft365 家庭版（RTL版）依照以下命令升级为专业版（VOL版）并激活。

1.打开命令提示符(管理员)执行以下命令进入OSPP.VBS目录
```
cd C:\Program Files\Microsoft Office\Office16
```

2.将Office365/Microsoft365家庭版RTL版转换为专业版VOL版

完成上一步骤后，执行以下命令转换版本。
```
for /f %x in ('dir /b ..\root\Licenses16\proplusvl_kms*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%x"
for /f %x in ('dir /b ..\root\Licenses16\proplusvl_mak*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%x"
```
提示：将以上代码中的“16”(Office2016 Office2019 LTSC2021 Office365/Microsoft365)改为“15”(Office2013)或者“14”(Office2010)，便可以将相对应的RTL版转换VOL版。

3.安装KMS激活密钥
```
cscript ospp.vbs /inpkey:XQNVK-8JYDB-WJ9W3-YJ8YR-WFG99
```

4.激活 Office
```
cscript ospp.vbs /sethst:kms.mcdu.xyz && cscript ospp.vbs /act
```

全新装机请直接部署VOL版，本文末有下载链接。不推荐RTL转VOL的方式装机。

#### 3.激活说明（激活原理）

KMS激活是微软针对大型企业（机构、政府、学校大量采购）设计的激活系统，KMS批量激活广泛用于机房服务器操作系统和大型企业内部批量激活员工电脑，限企业内网使用。

微软本意为，只要某台电脑运行在购买了KMS批量授权的企业内网，该电脑便被识别为该企业所有，自动占用一个授权名额，且无需任何操作自动永久激活。当该电脑搬离出企业超过180天后自动失去授权。此方案极大的方便了企业内部电脑的授权管理、IT资产管理，其设计精妙可谓拍案叫绝！

但，被分享到公网的KMS激活服务器，已通过技术手段突破了内网限制，不被内网约束。因此，只要你的电脑可以连接互联网，便不会失去授权名额。

KMS 激活有 180 天期限，此期限称为激活有效期间隔。若要保持激活状态，您的系统必须通过至少每 180 天连接一次KMS激活服务器来续订激活。
默认情况下，系统每 7 天自动进行一次激活续订尝试。在续订成功之后，激活有效期时间间隔将重新开始计算，重置为180天（详见微软官方文档）。

综上所述，只要您的电脑不超过 180 天以上无法连接企业内网（互联网），就无需进行任何操作，系统会自行续期保持激活状态。即永久激活。

如若你无法保证半年内上一次网，或者你有心理上的强迫症。那么下拉本文，按提示将你的电脑升级为中国政府版（仅支持Windows10系统）。
你只需要保证 410年 连接一次互联网，即可永久使用正版的Windows10系统。

#### 不支持 KMS 激活的 Windows/Office 版本：

Windows系统分为：MSDN版（面向开发者 很少见）、OEM版（面向笔记本品牌厂商 自带激活）、COEM版（正版光盘 激活绑定主板 很少见）、RTL版（零售正版光盘 一盘一Key一机 不绑定硬件）、VOL版（大客户版 企业政府学校机构大量采购）。其中我们常用的VOL版又分为专业版、企业版、教育版、中国政府版、欧洲版等等。Office情况类似不再复述。

KMS激活和MAK密钥激活是所有VOL版操作系统和Office套件的2种激活方式，本站教程所诉为KMS激活。零售版（RTL版）可通过更换密钥升级为VOL版（详见上文特例）。

快速区分Windows或Office原版镜像是否为VOL版：
1.镜像名称中包含 consumer、home、个人版、家庭版、旗舰版 都不是VOL版。
2.安装过程中，VOL版是不用输入密钥的，而RTL版会提示输入密钥。
3.镜像名称中有类似 business、vol、volume、批量、大客户 这样的英文或者中文标注 都是VOL版。

查看已安装的Windows或Office是否为VOL版：
1.查验Windows 在命令提示符执行：```slmgr /dlv```
2.查验Office 在命令提示符进入OSPP.VBS目录后执行：```cscript ospp.vbs /dstatus```
在“描述（DESCRIPTION）”这一行内有 VOLUME 字样就是VOL版，就是支持KMS激活。

对于绝大部分用户而言，Windows11/10只要不是家庭版（home版）在使用体验上不会感受到任何区别。企业版和教育版功能最多最全最完整最容易KMS激活。

请留意，本文末提供了常用的第三方微软Windows操作系统（Office套件）原版镜像库。可以下载到微软原版纯净镜像。

#### 为什么有人说 KMS只能激活半年（180天）到期后需要手动重新激活

使用“内网正版KMS激活”和“泄露出来的外网KMS激活”以及下文会提到的“非法伪造的未经授权的KMS模拟器激活”，激活成功后系统会每隔7天自动续期的，无需任何操作。也就是说你的系统会永远保持在174天以上的激活有效期，即永久激活，除非你断网180天。

但是除此之外，有大神研究出了“本机KMS激活”，就是让你下载安装一个KMS激活软件，软件会在你的电脑内生成一个虚拟机来伪造KMS主机，然后进行本机自我KMS激活。(在本机通过虚拟网卡的形式弄了个虚拟局域网给本机激活，又或者通过注册表劫持服务的形式让所有激活请求都劫持到本地。)

这简直是一个神作！它实现了离线KMS激活，突破了微软不允许自我激活的限制，不使用网络、不依赖任何KMS服务器。但也有它的缺点：

1.本机KMS虚拟机显然没必要一直在后台运行耗费电脑资源。因此就出现了上文描述的问题 “一次只能激活180天 到期后需要手动重新激活”，当然，也可以通过Windows计划任务，每隔一段时间自动运行续期。
2.激活软件在传播、修改、汉化过程中，非常容易被恶意植入捆绑后门、病毒。并以激活系统的名义理直气壮的要求用户忽略报毒、诱导用户关闭杀毒软件，长期在系统后台运行未知服务。
3.微软对该种软件的封杀力度很大，在系统升级或者Windows Defender升级时会被查杀而使激活失效。

所以，除非迫不得已，不建议使用这种软件。且一定要在软件作者发布页下载原版。

为什么网络上有一些软件可以KMS激活系统 19年、38年？

上文我们解释了什么是“激活有效期间隔”，Windows正常的VOL版本激活有效期间隔是180天，但除此之外还有一些特殊版本的系统。这些版本的Windows系统是专门为某些机构定制的，比如中国政府定制的神州网信政府版Windows10激活有效期间隔就是410年！

有了特殊版本，也就为漏洞敞开了大门。一些大神可以通过提取、替换系统根证书的方式偷梁换柱，更改普通VOL版本Windows的“激活有效期间隔”。(KMS38是利用了gatherosstate.exe漏洞)

根证书路径：
C:\Windows\System32\spp\tokens\skus
证书更新命令：
```
slmgr /rilc
```

顺便提一下"数字权利"激活吧：

数字权利是在Win10刚出来的时候，给Win7升级免费升级到win10搞出来的东西。正常来说你需要有一个正版的win7或者win8等系统，然后升级，程序会收集你电脑的硬件信息和密钥，生成一个"免费门票"提交给微软服务器，以后联网微软就可以判断硬件信息是否对的上就能激活。(要是你的key来源不怎么干净，这就相当于偷渡洗白了。)然而这枚免费门票是由 gatherosstate.exe 生成的，想必你也猜到了，破解这个系统应用就得到了盗版系统"数字权利"激活工具。

和自激活类KMS激活软件一样，这类软件在传播、修改、汉化过程中，同样非常容易被恶意植入捆绑后门、病毒。

#### 已永久激活的：

已通过数字许可证或者其它方式永久激活的系统，执行本文教程中的 KMS 激活命令不会影响和改变系统激活状态。
注意：更换密钥或者切换系统版本会导致失去原先激活状态！恢复方法为“先用命令行清除密钥卸载KMS激活，回到未激活状态。然后使用激活疑难解答”。

#### 微软官方文档：

[Windows] https://learn.microsoft.com/zh-cn/windows/deployment/volume-activation/activate-using-key-management-service-vamt
[Windows] https://learn.microsoft.com/zh-cn/windows/deployment/volume-activation/use-the-volume-activation-management-tool-client
[Windows] https://learn.microsoft.com/zh-cn/windows/deployment/volume-activation/volume-activation-windows-10
[Windows] https://learn.microsoft.com/zh-cn/windows/deployment/volume-activation/activate-windows-10-clients-vamt
[Windows] https://learn.microsoft.com/zh-cn/windows/deployment/volume-activation/plan-for-volume-activation-client
[Windows] https://learn.microsoft.com/zh-cn/windows-server/get-started/kms-activation-planning
[Windows] https://learn.microsoft.com/zh-cn/windows-server/get-started/kms-client-activation-keys
[Office] https://learn.microsoft.com/zh-cn/deployoffice/vlactivation/plan-volume-activation-of-office
[Office 2016/2019] https://learn.microsoft.com/zh-cn/DeployOffice/vlactivation/gvlks
[Office 2013] https://learn.microsoft.com/zh-cn/previous-versions/office/dn385360(v=office.15)
[Office 2010] https://learn.microsoft.com/zh-cn/previous-versions/office/office-2010/ee624355(v=office.14)
[Windows] https://learn.microsoft.com/zh-cn/search/?terms=kms

#### 4.Windows10 升级为政府版并激活410年

注意：中国政府版（Windows10神州网信政府版（CMGE））更新服务器位于中国境内，该版本移除、禁用了原版Windows10中自带的办公类、个人助理类、娱乐生活类应用以及基于云的服务（如：OneDrive,Windows Defender等），内置了中国政府指定数字证书机关的根证书，开启或者关闭了大量系统安防方面的设置。

官方文档：http://document.cmgos.com/release_notes/release_notes

1.升级。使用 Win+i 快捷键打开「设置」- 点击「更新和安全」- 在左侧点击「激活」选项卡。

点击右侧的「更改产品密钥按钮」- 输入密钥：YYVX9-NTFWV-6MDM3-9PT4T-4M68B

如果提示密钥错误，请先输入如下密钥升级为专业版后，再输入中国政府版密钥进行升级
VK7JG-NPHTM-C97JM-9MPGT-3V66T

2.激活。按提示升级后打开命令提示符(管理员)逐行执行以下命令：
```
slmgr /ipk YYVX9-NTFWV-6MDM3-9PT4T-4M68B
slmgr /skms kms.mcdu.xyz && slmgr /ato
```

执行以下命令查看KMS激活期限
slmgr /xpr

温馨提示：
你也可以直接使用原版 Windows10 神州网信政府版系统镜像安装系统，只需执行以下命令即可激活410年授权。
slmgr /skms kms.mcdu.xyz && slmgr /ato
支持最新的 V2022-L 版，在下文可以找到官方原版系统镜像的下载链接。

通过"升级转换"方式激活的政府版事实上是一个混合版，兼具两者特性，且不具备原本政府版严格的安全策略，更适合普通用户使用。

#### 5.激活失败如何排错

1.你的Windows/Office是否是批量VOL版本；
2.是否以管理员权限运行cmd命令提示符；
方法1:点开开始菜单，在搜索框中输入“cmd”，在搜索结果中，对着命令提示符程序，单击鼠标右键，菜单中点击选择“以管理员身份运行”；
方法2:点开开始菜单，再点击“所有应用”（Win7为所有程序），在“Windows系统”（Win7为附件），找到并右键单击，菜单中选择“以管理员身份运行”；
3.你的Windows/Office是否修改过/未安装GVLK KEY ；
4.检查你的网络连接；
5.本地的解析不对或网络问题；
6.根据出错代码自己搜索出错原因；
https://learn.microsoft.com/zh-cn/windows-server/get-started/activation-error-codes
https://answers.microsoft.com/zh-hans/windows/forum
0x80070005错误一般是你没用管理员权限运行cmd；
7.部分服务器类操作系统（如 数据中心版操作系统 Windows Server 2019 Datacenter）激活前需要先开放防火墙（开启ICMP回显 即打开ping）；
命令提示符(管理员)执行命令：netsh firewall set icmpsetting 8
8.部分idc商家的服务器操作系统会遇到无法使用外网KMS激活的问题，可以尝试更换安装镜像，或者联系idc客服为你激活。
9.本文中提到的所有命令应该在“cmd命令提示符”中执行，而非“Windows PowerShell”。当在“Windows PowerShell”中执行时，需要把“&&”替换为“;”。


#卸载 Windows KMS 激活
打开命令提示符(管理员) 逐行执行以下命令
slmgr /upk
slmgr /ckms
slmgr /rearm
然后重启电脑

#卸载 Office KMS 激活
1.打开命令提示符(管理员)进入 Office OSPP.VBS目录，执行以下命令查询激活密钥后五位（可能是多个）
cscript ospp.vbs /dstatus
2.继续执行以下命令
cscript ospp.vbs /unpkey:密钥后五位
cscript ospp.vbs /remhst
cscript ospp.vbs /rearm
