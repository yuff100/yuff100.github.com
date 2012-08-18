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
Eric P. Allman (Sendmail): Eric Allman是sendmail、syslog、trek最初的作者，也是Sendmail公司的共同创始人。他在“开源软件”这个术语出现之前就已经在编写开源软件了。他是ACM Queue编辑审查委员会的成员，并且是加州大学伯克利分校的演艺机构Cal Performances的理事会成员。他的个人主页是：http://www.neophilic.com/~eric

Keith Bostic (Berkeley DB)：Keith是加州大学伯克利分校计算机系统研究组（Computer Systems Research Group）的成员，是2.10BSD的架构师，4.4BSD的核心开发人员。获得了高等计算机系统协会的终身成就奖（the USENIX Lifetime Achievement Award ("The Flame")），表彰他对Unix社区所做的卓越贡献。获得了加州大学的杰出贡献奖，表彰他对4BSD的开源。Keith是著名的开源嵌入式数据库Berkeley DB的架构师和早期开发者之一。

Amy Brown (editorial)：Amy在滑铁卢大学获得数学学士学位，在软件行业有十年经验。她现在主要工作是写书和编辑，有时候会写一些关于软件的文章。她现在住在多伦多，有2个孩子和一只老猫。

C. Titus Brown (Continuous Integration): Titus的研究方向是进化模型、物理气象学、发育生物学、基因组学、生物信息学。他现在是密歇根州立大学的助理教授，在这里他正在研究几个感兴趣的新领域，包括科学软件的再现性和可维护性。他还是Python软件基金会的成员。他的blog是：http://ivory.idyll.org/

Roy Bryant (Snowflock): Roy做了20年的软件架构师和CTO，设计的系统包括Electronics Workbench (现在是国家仪器公司的Multisim)和Linkwalker Data Pipeline，后者获得了2006年的微软高性能计算全球用户大奖。在卖掉了最近一个创业公司以后，他回到多伦多大学计算机学院读研究生，主要研究方向是虚拟化和云计算。最近，他在2011年的ACM's Eurosys大会上发布了Snowflock的Kaleidoscope扩展。他的个人主页是：http://www.roybryant.net/

Russell Bryant (Asterisk): Russell是Digium公司的开源软件组的工程经理。他从2004年秋天开始成为Asterisk开发小组的核心成员。他几乎为Asterisk的所有方面做出过贡献，从项目管理、核心架构设计到开发。他的blog是：http://www.russellbryant.net/

Rosangela Canino-Koning (Continuous Integration)：在软件行业打了13年苦工以后，Rosangela回到了密歇根州立大学攻读计算机科学与进化生物学的博士学位。业余时间她喜欢阅读、徒步、旅行、hack开源生物信息软件。她的blog是：http://www.voidptr.net/

Francesco Cesarini (Riak): Francesco Cesarini从1995年开始使用Erlang进行日常开发工作，参与过爱立信的各种各样的项目，包括OTP R1。他是Erlang Solutions的创始人，以及O'Reilly出版的Erlang Programming的联合作者。他现在的工作是Erland Solutions的技术总监，有时候在英国牛津大学和瑞典哥德堡信息技术大学（IT University of Gotheburg in Sweden）教授研究生和本科生。

Robert Chansler (HDFS): Robert是雅虎的软件开发高级经理，在此之前他在卡耐基梅隆大学获得了分布式系统的硕士学位。他参与过众多项目：编译器（Tartan Labs）、打印与图像系统（Adobe Systems）、电子交易系统（Adobe Systems, Impresse）、网络存储管理系统（SanNavigator, McDATA）。在回到分布式系统领域，参与HDFS的开发之后，他发现在这些软件项目中存在几百甚至上千个类似的问题。

James Crook (Audacity)： James是爱尔兰都柏林的软件工程师。现在他正在开发电子设计相关工具，在此之前，他主要开发生物信息软件。他对于Audacity有许多大胆的设想。

Chris Davis (Graphite)： Chris是软件顾问、Google软件工程师，拥有12年的开发经验，设计、开发过具有可伸缩性的自动化监视工具。Ghris在2006年开始开发Graphite，并且一直领导该开源项目。在不写代码的时候，他喜欢烹饪、作曲、做研究。他的研究兴趣包括知识建模、群论、信息论、混沌理论和复杂系统。