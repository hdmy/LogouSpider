# LogouSpider
##**Node Spider，Python Random Forest, Echarts3 Visualization**   
##简介   
随机森林算法因具有自动降维、泛化能力强、训练速度快等特性，十分适用于对海量网络招聘信息进行分析研究，找出其中的规律，提供决策支持。  
为给IT行业求职者提供就业趋势分析以及薪资预测服务，本项目基于Node下网络爬虫技术，爬取拉勾网职业，以城市、职业类别、学历、工作经验、融资阶段、公司规模6维度特征为输入变量，建立随机森林分类模型，预测职位所处薪资水平，并以web页面为载体，使IT求职者可以自主预测。此外，本项目还将统计分析的结果可视化，表达潜在的就业趋势。通过与SVM、KNN、NB等分类算法的对比实验、具体招聘数据的测试证明，本项目所建立的随机森林模型是成功的，在薪资预测服务上有较高的可信度。
##技术亮点
- 数据爬取快——利用Node async模块高并发一次最多发出49个请求
- 薪资预测建模——采用Python sklearn随机森林分类算法（成熟度高），利用城市、工作经验、职业类别等6个特征建模，预测职位的薪资水平，并利用Node调用Python，使web页面能提供自定义的薪资预测。
- 数据可视化——利用fullPage.js、Echarts3生成直接的、交互的可视化环境，让数据更具吸引力、说服力。
- IP代理池，拉勾具有反爬措施，因此数据库MongoDB中需备有一定数量、有效的支持HTTPS协议、POST方法的IP，在爬取时利用superAgent模块发出代理请求。
- 每天定时更新爬取，利用node-schedule模块、Promise执行定时任务

##技术方案

![技术方案图](http://i.imgur.com/hCA3AN9.png)

##技术路线  
![技术路线](http://i.imgur.com/UMSn7Wy.png)

##使用方法    
安装所有相关模块

    npm install 

在开启MongoDB条件下,执行以下命令：  

数据爬取

	npm run crawler    //爬取拉勾，结束后统计分析，添加定时任务

爬取完毕后的数据分析

    npm run preprocess  // 数据预处理
    npm run analysis    // 模型训练、优化、验证、评估

数据可视化（PS: 如果只想看最终结果，直接执行此）

    npm run serve  // 自定义的薪资预测、统计分析数据可视化


##数据可视化的分析及结论
![各技术类职业总数量、平均薪资](http://i.imgur.com/5cS6O2x.png)


- 分析一：Java是互联网企业需求最旺盛的职业，约占技术类职业总量的1/5，可见该职业的热门程度。该现象造成的原因可能是近年来大数据、机器学习、人工智能等热门领域的兴起，Hadoop等大数据处理技术人才的需求缺口大。Web前端、测试工程师、PHP仅次于其后。  
在平均薪资上，CTO（首席技术官）位居第一，约为40.61万，其次是运维总监、技术总监、架构师，从侧面可以说明中国互联网行业的热度仍在不断上升，初创企业依旧在源源不断诞生，大公司中新产品的迭代依然迅速，企业仍需要资深的管理人员、总监来推进。
![Top 25热门技术类职位数量比、薪资比](http://i.imgur.com/zGKH9f4.png)


- 分析二：北上广深杭是互联网行业高速发展集中区，Java工程师是需求最旺盛的职业，这与分析1中的观点相对应。除此之外，web前端、测试工程师、PHP等职位在北京拥有最大的需求缺口。  
在平均薪资上，北京的职位总体比其他热门城市的职位高，结合该地区的经济情况看，其主要原因是北京房价高，买房压力大，消费水平高，在北京工作没有一定的经济水平难以生存。
![不同学历下的技术类职位数量比、薪资比](http://i.imgur.com/hHswEgW.png)



- 分析三：技术类职业对学历的要求不高，普遍要求为本科，平均薪资为16.91k，从侧面也说明了其中有着不少的高端职位，这也与技术开发重实践、轻理论相关。只要有过硬的技术水平，学历不会成为求职的门槛。
![不同工作经验下的技术类职位数量比、薪资比](http://i.imgur.com/jfeqS7U.png)


- 分析四：工作经验要求为3-5年、1-3年、5-10年的岗位居多，三者的平均薪资间隔约为6k。该类岗位往往是企业的中坚力量，5-10年的开发人员更是大公司的中高层、小公司的核心人员，技术类岗位更青睐有一定开发经验、具备核心竞争力的工程师。这也从侧面证明了互联网行业从10年前的野蛮生长到现在的逐渐成型、趋于稳定的发展状况。
![不同融资阶段的公司数量比、平均薪资](http://i.imgur.com/Ym7gXTP.png)


- 分析五：发布招聘信息的公司的融资阶段主要集中于初创型（未融资）、上市公司、成长型（不需要融资）、成长型（A轮），招聘需求重点在向大厂回归，创业型公司因发展需要保持有可观的招聘数量。   
处于成熟型（D轮及以上）的公司平均薪资最高，其次是成熟型（C轮）公司，这与大厂需要资深开发人员有关，企业更愿意开出高薪资招聘更适用的人才，淘汰较弱的员工。  
仅次于其后的是成长型（B轮）公司，该情况出现的原因主要从开发人员的心理谈起，在大厂长期工作、厌倦了“螺丝钉”式工作状态的开发人员更期待全新的项目挑战、高层的管理权，而这些很容易在小公司得到满足，而在高收入的促进作用下，资深的开发人员容易被高潜力的创业公司吸纳。
![web前端在不同工作经验下的平均薪资](http://i.imgur.com/N1OHXJ6.png)


- 分析六：应届生和一年以下的平均薪资约为6k，这与实际的招聘信息相符，每2年薪资的涨幅为6k,当工作经验为10年以上时，相比5-10年薪资有了大幅度增长，涨幅为11k。这从侧面说明了web前端工程师是个不错的职业，在积累了工作经验后更容易受企业青睐，升职加薪也比较顺利。 

结合上述6个分析，可以得出以下结论：  

1. Java是互联网企业需求最旺盛的职业，web前端、测试工程师、PHP仅次于其后。
2. 北京、上海、广州、深圳、杭州是互联网行业高速发展集中区。
3.	技术类职业对学历的要求不高，普遍要求为本科，只要有过硬的技术水平，学历不会成为求职的门槛。
4.	大多数技术岗位要求工作经验至少1年以上，企业更愿意开出高薪资招聘更适用的人才，淘汰较弱的员工。
5.	招聘需求主要集中在上市公司和刚刚发展的创业型公司。
6.	高潜力的创业公司因具有较强的挑战性，相应的岗位也具有较高的薪资。
