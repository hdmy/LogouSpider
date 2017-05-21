# LogouSpider
###**Node Spider，Python Random Forest, Echarts3 Visualization**
###简介
随机森林算法因具有自动降维、泛化能力强、训练速度快等特性，十分适用于对海量网络招聘信息进行分析研究，找出其中的规律，提供决策支持。  
为给IT行业求职者提供就业趋势分析以及薪资预测服务，本项目基于Node下网络爬虫技术，爬取拉勾网职业，以城市、职业类别、学历、工作经验、融资阶段、公司规模6维度特征为输入变量，建立随机森林分类模型，预测职位所处薪资水平，并以web页面为载体，使IT求职者可以自主预测。此外，本项目还将统计分析的结果可视化，表达潜在的就业趋势。通过与SVM、KNN、NB等分类算法的对比实验、具体招聘数据的测试证明，本项目所建立的随机森林模型是成功的，在薪资预测服务上有较高的可信度。
###技术亮点
- 数据爬取快——利用Node async模块高并发一次最多发出49个请求
- 薪资预测建模——采用Python sklearn随机森林分类算法（成熟度高），利用城市、工作经验、职业类别等6个特征建模，预测职位的薪资水平，并利用Node调用Python，使web页面能提供自定义的薪资预测。
- 数据可视化——利用fullPage.js、Echarts3生成直接的、交互的可视化环境，让数据更具吸引力、说服力。
- IP代理池，拉勾具有反爬措施，因此数据库MongoDB中需备有一定数量、有效的支持HTTPS协议、POST方法的IP，在爬取时利用superAgent模块发出代理请求。
- 每天定时更新爬取，利用node-schedule模块、Promise执行定时任务

###技术方案

![技术方案图](http://i.imgur.com/hCA3AN9.png)

###技术路线
![技术路线](http://i.imgur.com/UMSn7Wy.png)

###使用方法
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


###数据可视化部分结论

