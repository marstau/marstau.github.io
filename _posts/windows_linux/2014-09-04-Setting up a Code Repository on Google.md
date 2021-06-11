---
layout: post
title: Setting up a Code Repository on Google
category: 编程开发
tags: normal　knowledge
keywords: 
description: 
---

 



1.  访问[[http://code.google<span
    style="color:#000000;">.</span>com/](http://code.google.com/)],在此之前确保自己有一个google
    account.

2.  点击[Create a new project],跳转页面.

3.  键入[Project name]等。(Project
    name必须全部小写,且不能有空格),[Word verification]的两个单词是不用空格的.\
     **[Source Code License]**:

    **Apache License 2** 

    Apache License是著名的非盈利开源组织Apache采用的协议。该协议和BSD类似，同样鼓励代码共享和尊重原作者的著作权，同样允许代码修改，再发布（作为开源或商业软件）。需要满足的条件也和BSD类似：

    · 需要给代码的用户一份Apache License

    · 如果你修改了代码，需要在被修改的文件中说明。

    · 在延伸的代码中（修改和有源代码衍生的代码中）需要带有原来代码中的协议，商标，专利声明和其他原来作者规定需要包含的说明。

    · 如果再发布的产品中包含一个Notice文件，则在Notice文件中需要带有Apache License。你可以在Notice中增加自己的许可，但不可以表现为对Apache License构成更改。

    Apache License也是对商业应用友好的许可。使用者也可以在需要的时候修改代码来满足需要并作为开源或商业产品发布/销售。

    英文原文：<http://www.apache.org/licenses/LICENSE-2.0.html>

    Artistic License/GPL

    使作者保持对进一步开发的控制。

    英文原文：

    <http://www.perlfoundation.org/artistic_license_1_0>

    <http://www.perlfoundation.org/artistic_license_2_0>

    Eclipse Public License 1.0

    英文原文：[www.eclipse.org/legal/epl-v10.html](http://www.eclipse.org/legal/epl-v10.html)

    **GNU GPL v2**

    我们很熟悉的Linux就是采用了GPL。GPL协议和BSD, Apache License等鼓励代码重用的许可很不一样。GPL的出发点是代码的开源/免费使用和引用/修改/衍生代码的开源/免费使用，但不允许修改后和衍生的代 码做为闭源的商业软件发布和销售。这也就是为什么我们能用免费的各种linux，包括商业公司的linux和linux上各种各样的由个人，组织，以及商 业软件公司开发的免费软件了。

    GPL协议的主要内容是只要在一个软件中使用(”使用”指类库引用，修改后的代码或者衍生代码)GPL 协议的产品，则该软件产品必须也采用GPL协议，既必须也是开源和免费。这就是所谓的”传染性”。GPL协议的产品作为一个单独的产品使用没有任何问题，还可以享受免费的优势。

    由于GPL严格要求使用了GPL类库的软件产品必须使用GPL协议，对于使用GPL协议的开源代码，商业软件或者对代码有保密要求的部门就不适合集成/采用作为类库和二次开发的基础。

    其它细节如再发布的时候需要伴随GPL协议等和BSD/Apache等类似。

    英文原文：[www.gnu.org/licenses/gpl-2.0.html](http://www.gnu.org/licenses/gpl-2.0.html)

    **GNU GPL v3**

    与GNU GPL v2的区别如下：

    a、对用户的专利保护

    新版本GPL最重要的特性，就是明确了专利许可。任何分发GPLv3软件的人必须自动为软件用户提供许可证，让他们可以使用所有相关的专利。 从理论上来讲，这样做可以保护所有GPL专利享有者的诉讼权利，防止Linux经销商与专利持有者，如微软公司进行独家经营。

    b、不包含任何网络服务条款

    GPLv3的早期草案中包含了一个可选择条款，即要求所有的网络应用程序为远程用户提供源代码。如今，这个条款已被取消。幸亏如此，否则对于网络开发商和用户来说都会是极大的负担。尽管这样做的初衷是为了保证拥有此软件服务的用户享有的服务与二进制文件代表的服务完全相同，而这种做法却可能会 潜在地产生更为广泛的影响。

    但是，对SaaS用户提供源代码的要求并没有被放弃。FSF仍然要求进行Affero许可，而这个许可在GPL的基础上还增加了一项特别条 款。这或许是在告诫采取双重许可策略的经销商们，因为他们强烈激励服务供应商购买商业许可，而不是使用开放源代码版本。

    c、对DRM的限制

    绝大多数对GPLv3有争议的条款都涉及到对数字版权的管理。新版本的GPL并没有要求禁用DRM，但是通过两种非常重要的途径对它进行了限 制。

    首先是项声明，即基于GPL代码为基础的DRM不会构成一种“有效的技术手段”。这项声明旨在保证在DMCA和惩戒逆向开发DRM系统的法律 条款下，打破基于GPL代码为基础的DRM为合法。这项声明主要是针对用户的应用，但是如果它能够阻止使用DRM时对互操作性的限制，那么对企业用户来说 很有利。

    其次，要求应用GPL软件的家用设备必须允许用户执行他们自己修改的版本。这样做是为了阻止那些使用GPL代码、但需要由硬件供应商认可的设 备，如 TiVO等。但是，这只能影响到家用设备：供应商仍然能够利用数字签名来锁定GPL代码。这种差异都是缘于签署代码的开发者们拥有合法的安全应用程序，而 这恰恰是企业所需要的。

    英文原文：[www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

    **GNU Lesser GPL**

    LGPL是GPL的一个为主要为类库使用设计的开源协议。和GPL要求任何使用/修改/衍生之GPL类库的的软件必须采用GPL协议不同。LGPL 允许商业软件通过类库引用(link)方式使用LGPL类库而不需要开源商业软件的代码。这使得采用LGPL协议的开源代码可以被商业软件作为类库引用并 发布和销售。

    但是如果修改LGPL协议的代码或者衍生，则所有修改的代码，涉及修改部分的额外代码和衍生的代码都必须采用LGPL协议。因此LGPL协议的开源代码很适合作为第三方类库被商业软件引用，但不适合希望以LGPL协议代码为基础，通过修改和衍生的方式做二次开发的商业软件采用。

    GPL/LGPL都保障原作者的知识产权，避免有人利用开源代码复制并开发类似的产品

    英文原文：<http://www.gnu.org/copyleft/lesser.html>

    **MIT License**

    MIT是和BSD一样宽范的许可协议,作者只想保留版权,而无任何其他了限制.也就是说,你必须在你的发行版里包含原许可协议的声明,无论你是以二进制发布的还是以源代码发布的.

    英文原文：<http://www.opensource.org/licenses/mit-license.php>

    **Mozilla Public License 1.1**

    允许免费重发布、免费修改，但要求修改后的代码版权归软件的发起者。这种授权维护了商业软件的利益，它要求基于这种软件的修改无偿贡献版权给该软件。

    英文原文：<http://www.mozilla.org/MPL/MPL-1.1.html>

    **New BSD License**

    BSD开源协议是一个给于使用者很大自由的协议。基本上使用者可以”为所欲为”,可以自由的使用，修改源代码，也可以将修改后的代码作为开源或者专有软件再发布。

    但”为所欲为”的前提当你发布使用了BSD协议的代码，或则以BSD协议代码为基础做二次开发自己的产品时，需要满足三个条件：

    · 如果再发布的产品中包含源代码，则在源代码中必须带有原来代码中的BSD协议。

    · 如果再发布的只是二进制类库/软件，则需要在类库/软件的文档和版权声明中包含原来代码中的BSD协议。

    · 不可以用开源代码的作者/机构名字和原来产品的名字做市场推广。

    BSD 代码鼓励代码共享，但需要尊重代码作者的著作权。BSD由于允许使用者修改和重新发布代码，也允许使用或在BSD代码上开发商业软件发布和销售，因此是对 商业集成很友好的协议。而很多的公司企业在选用开源产品的时候都首选BSD协议，因为可以完全控制这些第三方的代码，在必要的时候可以修改或者二次开发。

    英文原文：<http://www.opensource.org/licenses/bsd-license.php>

    **Other Open Source**

    Common Development and Distribution License

    2005年，SUN公司宣布将开放操作系统Solaris的源代码，并推出CDDL（Common Development and Distribution License）作为Open Solaris的许可证。CDDL许可证是MPL许可证（Mozilla Public License，用来管理Mozilla网页浏览器及相关软件）的“升级版”。

    英文原文：<http://www.sun.com/cddl/cddl.html>

    Common Public License - v 1.0

    英文原文：<http://www.eclipse.org/legal/cpl-v10.html>

    还有微软的一些开源协议，这里就不列了，用的人不多，反正好像只有微软在用吧，哈哈

    大家可以根据自己的情况进行选择。

4.  点击[Create project]按钮之后，就完成了Project的创建.\
     注意： Google 的SVN 是强制开源的！

5.  现在就可以直接通过<https://code.google.com/p/marstau-ml-library/>访问刚刚创建的项目了，点击source可以看到如下图所示。\
     ![](http://files.note.sdo.com/XbPJ4~kgKKp2wE06E0025s)

    待会咱们就可以使用eclipse或者tortoiseSVN提交文件到<https://marstau-ml-library.googlecode.com/svn/trunk/>地址，并通过帐户密码进行update，需要注意的是，以后管理该项目的密码就是这里"googlecode.com password"帮我们生成的比较复杂安全性比较高的密码。另外一个地址：<http://marstau-ml-library.googlecode.com/svn/trunk/>给匿名用户checkout代码出来使用，只读权限。

6.  每次提交的时候都要通过"googlecode.com password"键入生成的密码提交.\
     XU6bN6Gx4Ze9








## Reference
* <http://code.google.com/p/support/wiki/GettingStarted#Getting_Started>

* <http://blog.csdn.net/deaboway/article/details/6347595>