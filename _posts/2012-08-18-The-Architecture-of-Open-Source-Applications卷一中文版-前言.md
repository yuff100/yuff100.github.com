---
layout: post
category : 翻译
tags : [The Architecture of Open Source Applications， 翻译]
date: 2012-08-18 13:51:00
---
{% include JB/setup %}

[原文地址](http://www.aosabook.org/en/intro1.html)

# 介绍 #
[Amy Brown](http://www.aosabook.org/en/intro1.html#brown-amy), [Greg Wilson](http://www.aosabook.org/en/intro1.html#wilson-greg)

  木工是一门严谨的手艺，甚至需要人们用一生的时间去学习、掌握。但是，木匠并不是建筑师。如果我们不考虑三角定线板和斜面接合等细节的话，建筑在很大程度上是设计出来的。建筑更类似于艺术，而不是工艺或者科技。

  编程同样是一门严谨的手艺，同样需要人们用一生的时间去学习和掌握，但编程并不是软件架构。许多程序员花费了多年时间思考（处理）重要的设计问题：应用可以被扩展吗？如果可以的话，应该提供一个脚本接口用来实现扩展吗？或者提供一些插件机制？或者其他一些方式？客户端应该做些什么？服务器端呢？“客户-服务器”模式对这个应用合适吗？这些都不是编程问题，就像决定把楼梯放在哪儿并不是一个木工问题一样。

  建筑架构和软件架构有很多的相似之处，但又有一个显著的不同。建筑设计师在职业生涯中通过学习数千个优秀的建筑设计来训练自己，但软件工程师只有很少的机会可以接触到大规模软件，更何况在很多时候，这些软件就是他们自己写的。软件工程师很少有机会可以接触到历史上的优秀软件，或者阅读由经验丰富的工程师所撰写的对这些软件设计的评论。这种现象所造成的结果就是软件工程师并没有吸取前人的教训，而是不断重复着别人的错误。

  这本书就是希望能改变这种状况。本书每一章都介绍了一个优秀的开源软件的架构：它的结构是什么样的？它的各部分之间是如何交互的？为什么这么设计？从中我们能学到什么？每一章的作者都是对该软件有充分了解的工程师，都有数十年设计、重构复杂软件的经验。这些开源软件的范围十分广泛，从简单的绘图软件、基于Web的电子表格软件到编译器套件和数百万行代码的可视化开发包。有些软件是近几年发布的，而有些软件已经发布了超过30年了。这些软件的共同点是它们的设计者都经历了漫长而痛苦的设计抉择，现在他们愿意与我们分享这些设计感悟，希望读者能够从这些设计抉择和感悟中有所收获。

## 本书作者包括： ##
*Eric P. Allman (Sendmail)*: Eric Allman是sendmail、syslog、trek最初的作者，也是Sendmail公司的共同创始人。他在“开源软件”这个术语出现之前就已经在编写开源软件了。他是ACM Queue编辑审查委员会的成员，并且是加州大学伯克利分校的演艺机构Cal Performances的理事会成员。他的个人主页是：http://www.neophilic.com/~eric

*Keith Bostic (Berkeley DB)*：Keith是加州大学伯克利分校计算机系统研究组（Computer Systems Research Group）的成员，是2.10BSD的架构师，4.4BSD的核心开发人员。获得了高等计算机系统协会的终身成就奖（the USENIX Lifetime Achievement Award ("The Flame")），表彰他对Unix社区所做的卓越贡献。获得了加州大学的杰出贡献奖，表彰他对4BSD的开源。Keith是著名的开源嵌入式数据库Berkeley DB的架构师和早期开发者之一。

*Amy Brown (editorial)*：Amy在滑铁卢大学获得数学学士学位，在软件行业有十年经验。她现在主要工作是写书和编辑，有时候会写一些关于软件的文章。她现在住在多伦多，有2个孩子和一只老猫。

*C. Titus Brown (Continuous Integration)*: Titus的研究方向是进化模型、物理气象学、发育生物学、基因组学、生物信息学。他现在是密歇根州立大学的助理教授，在这里他正在研究几个感兴趣的新领域，包括科学软件的再现性和可维护性。他还是Python软件基金会的成员。他的blog是：http://ivory.idyll.org/

*Roy Bryant (Snowflock)*: Roy做了20年的软件架构师和CTO，设计的系统包括Electronics Workbench (现在是国家仪器公司的Multisim)和Linkwalker Data Pipeline，后者获得了2006年的微软高性能计算全球用户大奖。在卖掉了最近一个创业公司以后，他回到多伦多大学计算机学院读研究生，主要研究方向是虚拟化和云计算。最近，他在2011年的ACM's Eurosys大会上发布了Snowflock的Kaleidoscope扩展。他的个人主页是：http://www.roybryant.net/

*Russell Bryant (Asterisk)*: Russell是Digium公司的开源软件组的工程经理。他从2004年秋天开始成为Asterisk开发小组的核心成员。他几乎为Asterisk的所有方面做出过贡献，从项目管理、核心架构设计到开发。他的blog是：http://www.russellbryant.net/

*Rosangela Canino-Koning (Continuous Integration)*：在软件行业打了13年苦工以后，Rosangela回到了密歇根州立大学攻读计算机科学与进化生物学的博士学位。业余时间她喜欢阅读、徒步、旅行、hack开源生物信息软件。她的blog是：http://www.voidptr.net/

*Francesco Cesarini (Riak)*: Francesco Cesarini从1995年开始使用Erlang进行日常开发工作，参与过爱立信的各种各样的项目，包括OTP R1。他是Erlang Solutions的创始人，以及O'Reilly出版的Erlang Programming的联合作者。他现在的工作是Erland Solutions的技术总监，有时候在英国牛津大学和瑞典哥德堡信息技术大学（IT University of Gotheburg in Sweden）教授研究生和本科生。

*Robert Chansler (HDFS)*: Robert是雅虎的软件开发高级经理，在此之前他在卡耐基梅隆大学获得了分布式系统的硕士学位。他参与过众多项目：编译器（Tartan Labs）、打印与图像系统（Adobe Systems）、电子交易系统（Adobe Systems, Impresse）、网络存储管理系统（SanNavigator, McDATA）。在回到分布式系统领域，参与HDFS的开发之后，他发现在这些软件项目中存在几百甚至上千个类似的问题。

*James Crook (Audacity)*： James是爱尔兰都柏林的软件工程师。现在他正在开发电子设计相关工具，在此之前，他主要开发生物信息软件。他对于Audacity有许多大胆的设想。

*Chris Davis (Graphite)*： Chris是软件顾问、Google软件工程师，拥有12年的开发经验，设计、开发过具有可伸缩性的自动化监视工具。Ghris在2006年开始开发Graphite，并且一直领导该开源项目。在不写代码的时候，他喜欢烹饪、作曲、做研究。他的研究兴趣包括知识建模、群论、信息论、混沌理论和复杂系统。

*Juliana Freire (VisTrails)*: Juliana是犹他大学计算机科学助理教授，在此之前，她是贝尔实验室数据库系统研究部门的研究员以及俄勒冈健康科学大学（OGI/OHSU）的助理教授。她的研究方向是种源（provenance）、科学数据管理（scientific data management）、信息集成以及Web挖掘。她获得过杰出青年教授奖以及IBM教师奖。她的研究由国家科学基金会、能源部、国家卫生研究院、IBM、微软以及雅虎资助。

*Berk Geveci (VTK)*: Berk是Kitware的科学计算总监。他现在负责领导ParaView（一个获奖的基于VTK的可视化应用）的开发工作。他的研究方向包括大规模并行计算、计算动力学、有限元、可视化算法。

*Andy Gross (Riak)*: Andy Gross是Basho技术公司的核心设计师，负责Basho的开源以及商业数据存储系统的设计研发工作。Andy于2007年12月份加入Basho，在此之前，他有10年的分布式系统工程经验。在加入Basho之前，Andy负责了多个公司的高级分布式系统工程，包括Mochi媒体公司、苹果公司以及Akamai技术公司。

*Bill Hoffman (CMake)*: Bill是Kitware的CTO和联合创始人。他是CMake项目的核心工程师，拥有超过20年的大规模C++系统开发经验。

*Cay Horstmann (Violet)*: Cay是圣何塞州立大学的计算机科学教授，但他经常离开学校，投入到实业工作中，或者到国外教书。他是多本程序设计书籍的作者，也是Violet、GridWorkd开源项目最初的作者。

*Emil Ivov (Jitsi)*: Emil是Jitsi（之前被称为SIP Communicator）项目的创始人和项目领导人。他还参与了多个其他项目，包括ice4j.org和JAIN SIP项目。2008年，Emil在斯特拉斯堡大学获得了博士学位，从那之后，他一直专注于Jitsi的相关事务。

*David Koop (VisTrails)*: David是犹他大学计算机科学专业的博士（2011年夏天毕业）。他的研究方向包括可视化、种源（provenance）以及科学数据管理。他是VisTrails系统的开发领导人之一，并且是VisTrails公司的高级软件架构师。

*Hairong Kuang (HDFS)*: Hairong Kuang是Hadoop项目的长期贡献者。她如今为Facebook工作，在此之前，她是雅虎的工程师。在投入实业工作之前，她是位于Pomona的加利福尼亚工业大学的助理教授。她在Irvine的加利福尼亚大学获得了计算机科学博士学位。她的主要研究方向是云计算、移动代理、并行计算、分布式系统等。

*H. Andrés Lagar-Cavilla (Snowflock)*: Andrés是一位软件系统研究员，在虚拟化、操作系统、安全性、网格计算、移动计算等方面拥有丰富的经验。他在阿根廷获得了学士学位，并且在多伦多大学获得了计算机科学的硕士、博士学位。他的个人主页是：http://lagarcavilla.org。

*Chris Lattner (LLVM)*: Chris是一位兴趣以及经验非常广泛的软件开发工程师，他接触的领域包括：编译工具链、操作系统、图形图像渲染等。他是LLVM开源项目的设计者和领导架构师。可以在http://nondot.org/~sabre/上看到更多关于Chris以及他的项目的内容。

*Alan Laudicina (Thousand Parsec)*: Alan是韦恩州立大学计算机专业的博士研究生，研究方向为分布式系统。他在业余时间写代码、学习编程语言、玩扑克。他的个人主页是http://alanp.ca/。

*Danielle Madeley (Telepathy)*: Danielle是一位澳大利亚软件工程师，现在为Collabora公司工作，工作内容包括心灵感应以及其他一些魔术。她拥有电子工程和计算机科学学士学位，并且喜欢收集长毛绒企鹅。她的博客是http://blogs.gnome.org/danni/。

*Adam Marcus (NoSQL)*: Adam是麻省理工学院计算机科学和人工智能实验室的博士研究生，他的研究方向包括数据库系统合集以及社会化计算。他现在的工作是尝试把传统数据库系统与一些新的数据源相连接，包括twitter等社会化数据流以及Mechanical Turk等人机计算平台。他喜欢将自己的研究原型扩展为一个可用的开源项目，并且他长期关注开源存储系统的进展。他的blog是http://blog.marcua.net。

*Kenneth Martin (CMake)*: Ken是Kitware的主席和CFO, Kitware是美国的一家研发公司，成立于1998年，Ken是联合创始人。Ken帮助这家公司成长为一家领先的研发供应商，客户包括众多政府部门和公司。

*Aaron Mavrinac (Thousand Parsec)*: Aaron是温莎大学电子与计算机工程的博士研究生，主要研究方向包括摄像网络、计算机视觉以及机器人等。在工作之余，他参与了Thousand Parsec以及其他一些用Python和C开发的自由软件的开发工作，以及用这些软件来做很多的有意思的事情。他的主页是http://www.mavrinac.com。

*Kim Moir (Eclipse)*: Kim在位于渥太华的IBM Rational软件实验室工作，职位是Eclipse和实时Equinox项目的发布工程主管，她还是Eclipse架构委员会成员。她的研究方向包括编译优化、Equinox以及基于编译组件的软件。工作之余，她喜欢和同伴一起跑步、公路徒步等。她的blog是http://relengofthenerds.blogspot.com/。

*Dirkjan Ochtman (Mercurial)*: Dirkjan在2010年获得计算机科学博士学位，之后他为一家金融创业公司工作了3年。 在业余时间，他喜欢研究Mercurial、Python、Gentoo Linux以及Python CouchDB库。他住在阿姆斯特丹的一个美丽的城市，他的个人主页是http://dirkjan.ochtman.nl/。

*Sanjay Radia (HDFS)*: Sanjay是雅虎的Hadoop项目架构师和研发工程师，同时也是Apache软件基金会项目管理委员会成员。在此之前，他是Cassatt、SUN、INRIA的高级工程师，开发了分布式系统、网格/效用计算基础构件等。Sanjay拥有加拿大滑铁卢大学计算机科学博士学位。

*Chet Ramey (Bash)*: Chet参与bash相关工作已经超过20年了，在最近的17年他一直是主要的开发者。他是俄亥俄州克利夫兰的凯斯西保留地大学的长期雇员，在那里他获得了学士和硕士学位。chet全家以及宠物居住在克利夫兰，他的主页是http://tiswww.cwru.edu/~chet。

*Emanuele Santos (VisTrails)*: Emanuele是犹他大学的研究科学家。她的研究方向包括科学数据管理、可视化和种源（provenance）。她在2010年在犹他大学获得了计算机博士学位。她还是VisTrails系统的开发主管。

*Carlos Scheidegger (VisTrails)*: Carlos在犹他大学获得了计算机博士学位，现在是AT&T研究实验室的研究员。Carlos在2007年获得了IEEE可视化杂志的最佳论文奖，在2008年获得了Shape Modeling International的最佳论文奖。他的研究方向包括数据可视化分析、几何运算、计算机图形图像等。

*Will Schroeder (VTK)*: Will是Kitware的主席和联合创始人。他的专业是计算科学家，后来他成为了VTK的核心开发人员。他热爱编写漂亮的代码，特别是和几何运算、图形图像有关的代码。

*Margo Seltzer (Berkeley DB)*: Margo是哈佛大学工程与应用学院计算机科学系的赫歇尔史密斯教授（Herchel Smith Professor），并且她是Oracle公司的架构师。她是Berkeley DB的核心设计者之一，并且是Sleepycat软件公司的联合创始人。她的研究方向包括文件系统、数据库系统、交易系统、医学数据挖掘等。她的职业生涯可以参考http://www.eecs.harvard.edu/~margo，她的blog是http://mis-misinformation.blogspot.com/。

*Justin Sheehy (Riak)*: Justin是Basho技术公司的CTO，Basho技术公司开发了Webmachine和Riak。之前，他是MITRE公司的核心科学家、Akamai的系统基础架构的高级架构师。他的主要研究方向包括了开发可靠的分布式系统的若干方面：调度算法、基于语言的形式模型、适应性等。

*Richard Shimooka (Battle for Wesnoth)*: Richard是位于安大略省金斯敦市的女王大学的防御管理研究项目的助理研究员，他还是开源游戏韦诺之战项目的副会长和秘书。Richard撰写了多篇关于社会团体的组织文化的文章，内容涵盖政府组织到开源项目组织。

*Konstantin V. Shvachko (HDFS)*: Konstantin是HDFS资深开发人员、eBay的Hadoop核心架构师。他专注于大规模分布式存储系统的高效数据结构和算法。他发明了一种新型的平衡树（S-trees），可以用于优化非结构化数据的索引。他同时还是一个基于S-tree的Linux文件系统（treeFS，一个reiserFS的原型）的核心开发人员。Konstantin在莫斯科国立大学获得计算机科学博士学位。他还是Apache Hadoop项目管理委员会成员。

*Claudio Silva (VisTrails)*: Claudio是犹他大学计算机科学的全职教授，他的研究方向包括可视化、几何计算、计算机图形图像、科学计算管理。他在1996年获得位于Stony Brook的纽约州立大学颁发的计算机科学博士学位。之后在2011年，他加入了纽约大学工学院，成为计算机科学与工程全职教授。

*Suresh Srinivas (HDFS)*: Suresh是雅虎的HDFS软件架构师，他是HDFS开发人员、Apache软件基金会项目管理委员会成员。在此之前，他为Sylantro系统公司工作，为通信服务开发可扩展基础架构。Suresh在印度卡纳塔克邦国立技术学院获得电子与通信学士学位。

*Simon Stewart (Selenium)*: Simon居住在伦敦，是Google的测试软件工程师。他是Selenium项目的核心开发人员，是WebDriver的创始人，对开源项目充满了热情。Simon喜欢喝啤酒和写代码，有时候他边喝啤酒边写代码。他的个人主页是http://www.pubbitch.org/。

*Audrey Tang (SocialCalc)*: Audrey是一个来自台湾的自学成才的程序员、翻译家。她现在为Socialtext工作，头衔是“没有头衔”（"Untitled Page"）。同时她还作为contractor为苹果做本地化和发布工程。之前，她设计、领导了Pugs项目（第一个Perl6实现）。她还为Haskell、Perl5、Perl6的语言设计委员会工作。另外，她在CPAN和Hackage上有众多项目。她的blog是http://pugs.blogs.com/audreyt/。

*Huy T. Vo (VisTrails)*: Huy在2011年5月获得了犹他大学颁发的博士学位。他的研究方向包括可视化、数据流架构、科学数据管理。他是VisTrails公司的高级工程师，同时他还是纽约大学工学院的助理研究教授。

*David White (Battle for Wesnoth)*: David是开源游戏韦诺之战的创始人和开发主管。他参与了多个开源视频游戏项目，包括Frogatto（他联合创始人）。David是Sabre控股公司的资深工程师、travel技术公司的主管。

*Greg Wilson (editorial)*: Greg在高性能科学计算、数据可视化、计算安全等领域拥有超过25年的经验，他还是多部书籍的作者（包括获得2008年Jolt大奖的《Beautiful Code》,以及2本写给儿童的书籍）。Greg在1993年获得爱丁堡大学颁发的计算机科学博士学位，他的blog是http://third-bit.com以及http://software-carpentry.org。

*Tarek Ziadé (Python Packaging)*: Tarek住在法国的勃艮第，他是Mozilla的高级软件工程师，主要工作是开发基于Python的服务器。平时，他领导Python的开发包分发工作。