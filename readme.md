# Welcome to NICS-EFC

> 这里是一些新人须知，以及该repository的索引

## 本Repo的指引

- 首先阅读本readme.md文件，明确其中内容
- for_admin
    - 里面是一些网管配置和管理服务器的记录，里面没有危险信息所以就开放了，**一般用户不需要看**
- for_newbies (实验室新人必备技能的一些tutorial)
    - software.md               - 各种常用软件
    - deep-learning.md          - 深度学习相关知识和工具
- for_eva_users (服务器资源申请和使用相关指南)
    - mail.md                   - 申请邮件模板
    - login.md                  - 关于如何登录服务器
    - login-tools.md            - 登录服务器的一些具体工具
    - eva-user-should-know.md   - 使用常识和用户须知
    - qa.md                     - 常见问题速查

- 本repo中的一些图片由github图床所维护，所以可能需要科学上网才可见(但由于本repo也在github上维护，所以理论上不会出现显示不出的问题)
    - 如果图没有load出来，check Ur VPN

# 如何……

## 如何成为实验室的一员

1. 注册实验室账号： 
    - 首先登录[实验室网站](https://nicsefc.ee.tsinghua.edu.cn/),点击主页上的Internal，或者直接点击[这个连接](https://nicsefc.ee.tsinghua.edu.cn/internal/auth/login/) 自助注册实验室账号。
    - 其中有验证问题，答案**请咨询你的负责研究生**
    - **注意：** 
      - 实验室账号密码也是你将来登录服务器资源的密码，所以请**妥善保管，且不要使用弱密码！**
      - 用户名也请不要使用过于简单的，如你的名字拼音开头，可能会存在重名问题以及安全隐患，建议采用全名+年份，如zhongkai19
      - 悲惨案例：2021-09, 由于合作老师的同学使用了弱密码，导致被其他人暴力破解登陆上服务器并使用服务器挖矿
2. 完善信息
    - 注册好实验室账号之后，请填写 [NICS实验室Profile](http://nicsefc.ee.tsinghua.edu.cn/internal/profile/)，你的信息将出现在[NICS实验室人员](https://nicsefc.ee.tsinghua.edu.cn/people/) 中

## 如何使用计算资源

> 我刚进组？想要用GPU/CPU服务器资源，如何申请？

* 首先请记住带你进组的研究生同学是谁，之后的一些步骤可能都要麻烦他，记得礼貌感谢

* 注册实验室账号(参考上一个section)

* 了解实验室服务器基本概念
  * **请务必阅读下一段文字并理解其中部分定义的含义，否则你将无法正常理解与使用服务器**
  * **如果你对其中的某些概念一头雾水，先Google一下他们**
  * 实验室服务器管理方式：我们采用了LXC （Linux Container）进行用户环境隔离。这一概念类似Docker或虚拟机，但是更为轻量级，实际上是Docker早期的底层技术。计算资源以Container（容器）为单位进行管理和使用，以保证各个项目的代码环境不会互相影响，用户所使用的是Container，而服务器的主机仅网管有权限进行登录。我们将Container配置成等效于一个独立的系统，拥有自己的域名、IP，使用者可以拥有sudo权限以及进行大部分操作（危险操作除外）
  * 登录基本常识：使用时采用ssh的方式从你的个人电脑远程登录服务器(直接登录Container即可，不需要理会主机），所以你需要了解ssh的使用方式，并找到适合你的ssh软件
  * 系统基本常识：实验室服务器系统为Ubuntu（包括16.04，18.04，20.04），一般没有图形界面，所以你需要学习Linux系统基本概念和基于命令行的Ubuntu基本使用方法

* 申请与使用服务器资源

  1. 申请服务器资源之前，请确认如下几件事情：

     * 我目前有项目(科研)需要使用服务器资源，并且我对该项目所需要的环境要求以及硬件要求有所了解 (如果你不清楚，**咨询你的负责研究生，或者让你的负责研究生代为申请**)
     * 我对Linux系统与ssh有基本的了解
     * 我清楚拥有sudo权限之后的一些危险操作可能会让整个系统崩溃，从而影响到自己以及其他人的开发，我会在执行可能的危险操作时思考/提问。
     * 我知道服务器可能不稳定，我会妥善做好自己生产环境，代码和数据的备份

  2. 申请服务器资源有两种方式: 1）申请一个独立的Container，相当于新建你自己的一套Linux系统 2）共享他人的Container，相当于在linux系统中加入了一个新的用户

     * 由于服务器资源以及管理成本的原因，如果没有充分理由，网管将不会许可任意同学申请新的Container。如果你需要新建一个自己的Container，需要参考下一步，向网管**发邮件申请**。建议以项目，或者小组为单位进行申请。
     * 网管**鼓励第二种方式**。如果想要加入其他人的Conatiner，不需要向网管进行邮件申请，只需要联系Container的所有者(比如你的负责研究生)，让TA在`/etc/login.user.allow`中加入你的**实验室账号用户名**，你就可以获得他Container的登录权限了。如果想要sudo权限，同样让他在`/etc/sudoers`中仿照其他sudo用户加入你的用户名即可。

  3. 发送邮件申请： 

     * 请参考该repo下的 [for_eva_users/mail.md](./for_eva_users/mail.md)中按照邮件格式，将**其中所有内容填充之后**，发送给网管 `zhongk19@mails.tsinghua.edu.cn`  `suozhang1998@gmail.com`, 并且**抄送你的负责研究生**。网管会回复你的诉求。
     * 如果通过审核之后，网管会邮件回复给你，你的container的域名以及当前的IP，你可以用他们来登入服务器。

  4. 日常使用：

     * 申请Container/联系他人加入Container之后，参考[for_eva_users/login.md](./for_eva_users/login.md)以及[for_eva_users/login-tools.md](./for_eva_users/login-tools.md)尝试登录服务器

     * 可参考[for_eva_users/eva-user-should-know.md](./for_eva_users/eva-user-should-know.md)了解用户须知并安装自己的环境并注意关键问题
     * 遇到的各种问题，都参考[for_eva_users/qa.md](./for_eva_users/qa.md)
     * **请联系你的负责研究生将你拉入nics-server微信群**，该群可以进行服务器问题的讨论，非必要或十万火急，请不要私聊网管提问服务器问题。(网管会把本链接丢给你，让你自己看)

  5. **上手体验方案**：如果你是新同学，还只是刚进组了解工作情况的状态，但是你想先上手体验和练习一下Linux系统使用，不想mess-up负责研究生的环境。这么好学的行为，网管怎么会不鼓励呢！请联系网管(在nicsefc-server群中)，将你的名字加入到sandbox container当中。之后用你的名字登录`sandbox.eoe0.nics.cc`,就可以开始进行学习了。(注意: 这个环境也会坏，而且是所有新同学共享的playground，所以，**不要肆意妄为！**) 另外，这个环境下的配置是不可以一键迁移到其他环境中的，所以像它的名字一样，请你把它当成一个”沙盒“。

* 登录服务器：由于涉及到较多概念与操作，单开一个文件，请参考本repo的[for_eva_users/login.md](./for_eva_users/login.md) 

## 如何提问交流

> 很多时候，服务器不可避免的可能出现包括登录不上以及出现各种问题的可能性，当出现问题时，为了问题尽快解决以及你个人与网管的血压安全，**请遵循以下步骤**、

- 先**说点不好听的**
    - 服务器有可能因为各种原因会挂(学校机房硬件问题，系统稳定性问题，其他同学在container内误操作问题)，但是这些问题**不是网管造成的问题**，网管理解因为服务器问题耽误了工作进度会使人急躁，但提问时候，请不要发出诸如“学长，服务器怎么又挂了”的抱怨。网管不是全职网管，**没有义务解决你的所有问题**，所以提问时，请进行询问而不是质询。
    - 提问是一种艺术，提问时候，请**先自行充分debug，并描述清楚你的问题**(当前问题的现象，报错信息，你猜测的可能原因，并且查询了qa page)，并给出**可能帮助解决这个问题你知道的辅助信息** (比如“昨天晚上10点左右登录是正常的，我上次登录的时候跑了几个比较耗GPU的程序，可能调用了xxx”)
    - 当然网管可能会因为能力有限而不能对一些问题进行自动处理，但基本会给出可行的解决方案(即使dirty)。如果你足够有能力，你可以将自己发现的**可行的解决方案**或提交给网管，我们将洗耳恭听并加入qa page加以推广。
    - 网管不会配置环境，出现了报错先自行进行搜索和debug，**初步判断是Container内的环境问题还是与服务器主机有关**。网管**不负责帮忙配环境！**，请你推测出**你的问题可能会与LXC环境有关或者环境出现明显问题**，再在群里进行提问。

0. 先自己思考或者Google(能不baidu尽量不baidu)问题可能出现的原因，排除掉自己误操作可能性。
1. 查看本repo的[for_eva_users/qa.md](./for_eva_users/qa.md)（建议收藏该page），自查有没有自己的问题，如果有，先按照解决方案进行操作
    - 对于一些比较general的问题，如（我cuda怎么用不了了？我的服务器怎么登录不上了？），请**仔细阅读qa，并尝试并给出报错信息再提问**，比如nvidia-smi的报错信息，或是usereg登录时候的报错信息，能否ping通ip？
2. 在nics-server微信群内，提问
3. 如果你担心自己的问题比较愚蠢，咨询自己的负责研究生问题的解决方案 (为了他的血压，请完成第一步之后再执行此操作)
3. 如果他也不能解决，在群里提问

## 如何参与编辑本文档

- 我们**非常欢迎**其他同学参与补充此文档(你遇到的一些问题以及解决方案/你想和大家分享的素材和资源)，那么如何参与编辑呢？(注意，以下部分涉及到一些git的知识，请预先了解)

- 为了防止大家的误操作，我们对此repo进行权限控制，不允许用户直接push到本repo，所以推荐大家使用**pull request**的方式进行补充
    - 具体实现方式: fork一份本repo到你的账户，并且在你的账户下进行commit与push到远端；
    - 然后在github page中，选择"pull request"提交一个request: 7  
    - 然后私聊或者在nics-server群中提醒网管查看commit，并决定是否merge

![](https://github.com/A-suozhang/MyPicBed/raw/master//img/20211017134831.png)

