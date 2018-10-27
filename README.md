### 搭建酸酸乳上某国外搜索网站//自建吃鸡加速服务器教程


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eafc435f46cb?w=1200&h=750&f=png&s=831363)

关于vps，我这边用过好几个国内外知名大公司的（免费的没用过，便宜没好货，即使天上掉馅饼的好事，估计我也捡不到，所以还是不考虑了），最后还是觉得vultr的比较好，性价比高。搬瓦工的话，便宜是便宜，但是是半年一年的卖，现在封的严，运气不好今天买的明天就不能用了，所以不推荐...其他的不说了，性价比不高。

关于vultr还有几点好处。

1.支持支付宝付款

2.vultr实际上是折算成小时来计费的，比如服务器是5美元1个月，那么每小时收费为5/30/24=0.0069美元 会自动从账号中扣费，只要保证账号有钱即可。如果你部署的服务器实测后速度不理想，你可以把它删掉（destroy），重新换个地区的服务器来部署，方便且实用。因为新的服务器就是新的ip，所以当ip被墙时这个方法很有用。

所以本篇教程以vultr为例。

下面，我将教大家如何一步一步的搭建酸酸乳服务器科学上网。



为防止文章被锁定，以下全部使用别名：



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb01250149e8?w=539&h=94&f=png&s=56676)

他们俩有啥区别：功能都一样，最早出来的是原版酸酸乳，后来有人在其基础上多加了一个协议，变成了酸酸乳，据说可以防止ip被封。

第一步 注册vultr并充值

打开[vultr官方网址](https://www.vultr.com/?ref=7568358)并注册账号 ，上文提到过，vultr是支持支付宝的，所以这里给出支付宝充值的示例图。


界面虽然是英文的，但是肯定难不倒各位小伙伴，何况浏览器还有翻译功能，所以注册的图我就不放了。

接下来是充值，这是必须的，不多bb（这里最少充值10美元）


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb05e674e572?w=1240&h=613&f=png&s=110234)

第二步 新建vps服务器
点击右上角加号，新建一个服务器

![](https://user-gold-cdn.xitu.io/2018/10/23/1669ed7cf6f720e3?w=1240&h=613&f=png&s=118413)

这里可以选择各个大洲的服务器。推荐两个，一个是日本，一个洛杉矶。

日本的节点好处是延迟很低，大概在80-120左右，但是掉包率有点高。

洛杉矶的节点延迟大概在120-220左右，掉包率低，几乎不掉包。

其他的节点也可以试试，比如硅谷也不错，虽然延迟高了点，但是不容易被墙，很稳定。

如果需要打游戏加速，请选择延迟低的节点

2018-1-25更新

昨天早上很多ip被qiang，请大家不要选亚洲节点，即jp和新家坡的。可以尝试一下冷门的，比如悉尼、澳大利亚等



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb1cc006c6f2?w=1240&h=613&f=png&s=223884)

接下来选择vps的操作系统和套餐，没啥说的，选择centos6 64位操作系统，然后选择5刀或其他的套餐，目前迈阿密和日本好像还有2.5刀一个月的。

套餐价格不仅仅跟流量多少和配置等明面上的信息有关，跟分配的vps的带宽也有关，比如$5比$2.5的带宽就高，速度也更快，如果是个人或3人以下使用，建议5刀（速度还行）的，多人（5-8）可以选择10刀的(速度贼快)。

总之就是，越贵的，分配的带宽越高，看自己需求来吧，我目前是用的10刀的。


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb220c4b91e5?w=1240&h=733&f=png&s=302109)


最后点击立即创建



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb24bed9259a?w=1240&h=83&f=png&s=46937)

过一段时间后，服务器创建完成。

第三步 部署服务器
紧接上一步，服务器新建完成后，点击下图的菊花图标，查看详情（要等到右边的绿色文字变为Running之后点击）


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb271b3985d9?w=1240&h=613&f=png&s=130433)

下面是服务器详细信息，需要说明的是服务器IP、用户名和密码，下面会用到的


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb295986e93d?w=1240&h=601&f=png&s=183185)

接下来你需要下载一个叫直接下载到桌面就行。

[ PuTTY_0.67.0.0.exe]( https://www.bbaaz.com/forum.php?mod=attachment&aid=MzR8OGQ2MWZjYTV8MTU0MDYwMDg1OXwwfDIy)

(518.91 KB, 下载次数: 4592)

![](https://user-gold-cdn.xitu.io/2018/10/27/166b31ebea062bfb?w=452&h=435&f=png&s=33297)

SSH工具连接教程

下载上面的SSH连接工具到桌面，双击打开，有的电脑需要选择管理员运行。

然后会看到登录窗口，下图：
 
![](https://user-gold-cdn.xitu.io/2018/10/27/166b31ef2974aa2c?w=660&h=416&f=png&s=9160)

如图所示，我们填写我们的服务器IP，然后选择open登录。

就会看到如下窗口，初次登录会提示你是否登录，选择是就可以。
 

然后我们输入统一帐号：

root
输入后按回车确定

在然后我们输入密码：输入的密码我们是看不到的，你直接输入密码按回车就可以，出现以下窗口说明登录成功。


![](https://user-gold-cdn.xitu.io/2018/10/27/166b31f58405c4a9?w=661&h=416&f=png&s=30967)



PS：
不是所有的主机都是这个页面，不同的主机商系统提示不一样，只要出现

root@xxx
#
什么的都是登录成功了。


常见连接错误解决方法：


如果连接上不，可能是以下问题导致的。

1、看你的VPS连接端口是不是22（一般主机商都是22），搬瓦工的VPS是5位数的端口，可以在后台或者邮箱查看。


连接上后密码提示错误主要是因为你输入的方法是错误的。

解决方法：复制密码，然后粘贴，然后回车。（在连接工具中密码是看不到的，粘贴后直接回车就行，鼠标右键是粘贴，点击一次就可以，不要多次点击。）


接下来分享一段一键部署服务器的代码，是中文版的，功能很强大，感谢作者，推荐大家使用

斜体加粗部分为代码，大家直接全部复制，然后按回车键

【一键部署酸酸乳代码】

CentOS/Debian/Ubuntu 酸酸乳单/多端口一键管理脚本：

--------------------以下区域全部复制--------------------------------

yum -y install wget

wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
复制代码
----------------------------------------------------------------------

备用下载地址：

--------------------以下区域全部复制--------------------------------

yum -y install wget
wget -N --no-check-certificate https://softs.wtf/Bash/ssr.sh && chmod +x ssr.sh && bash ssr.sh
复制代码
-----------------------------------------------------------------------

安装成功之后显示如下图，如果下次还想调出此界面，输入 bash ssr.sh



接下来我们一起来设置相关信息，照着图走就行











然后就会开始部署酸酸乳了，耐心等待一会，到这一步，输入y，然后再继续耐心等待2分钟左右





到这一步会卡一下





复制下图的连接信息到记事本





最后一步 安装g**gle BBR加速酸酸乳
下面加粗斜体部分，整个复制，粘贴进控制台，然后会自动运行

【g**gle BBR加速教程】
--------------------以下区域全部复制--------------------------------

yum -y install wget

wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

chmod +x bbr.sh

./bbr.sh

------------------------------------------------------------------------

到下面这里需要按一下回车键





按任意键确定安装





接下来等待安装即可，哦对了，这里也会卡一会



安装完成如下图，最后输入y重启服务器即可





好了，到这里，酸酸乳安装大工搞成

最后一步 使用酸酸乳科学上网

这里是“酸酸乳”的下载地址及教程

https://github.com/woshijiuge2018/-2019/blob/master/README.md


好了，教程到此结束，谢谢大家的兹辞

================================================================

========切记一定不要利用本教程作出有损中华人民共和国利益的事情==========

=========切记一定不要利用本教程作出有损中华人民共和国利益的事情=========

=========切记一定不要利用本教程作出有损中华人民共和国利益的事情=========

===================请大家做一个遵纪守法的合格公民====================

================================================================

有朋友反馈说连不上，具体原因我也搞不懂呢。。免费的用的人多，限速。如果想用高速且稳定的酸酸乳账号并且条件允许，建议自行购买VPS服务器搭建梯子。有问题的私信我留下QQ吧，赞赏随意金额，楼主可加你远程协助帮你们解决~

![](https://github.com/jp4593425/USmilk/blob/master/QQ%E5%9B%BE%E7%89%8720181023114540.png
)

关于上不去网

如果有一天你本来用得好好的，突然发现连不上google了，那估计是ip被qiang了，这只能重新开一个ip了，之前的可以destory，新开服务器多收$0.02，大概也就1毛钱吧

请大家不要在评论里恢复一些关键字眼，文章会被删
===问题区===
有的说搭完了上不去网的，可以这么排查下问题

1.右键小飞机图标，看是否已"启用系统开启代理"，如果开启了还是不行，把“系统代理模式”改成“全局模式”（默认是pac模式），再试试能不能上g00gle

2.看ip是否ping的通，ping不通代表被qiang了，只能destory后重新部署一次

3.在服务器上输入bash ssr.sh查看是否安装好酸酸乳，如图




4.如果上述都没问题，在上图的时候，输入3，卸载酸酸乳，卸载完成后，再输入bash ssr.sh, 输入1 ，再安装一次，应该就可以了
