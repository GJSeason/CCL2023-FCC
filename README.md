# CCL 2023 电信网络诈骗案件分类评测

##### 组织者：孙承杰 sunchengjie@hit.edu.cn

##### 负责人：孙承杰 sunchengjie@hit.edu.cn

##### 联系人：纪杰 jijie@insun.hit.edu.cn

## 目录

- [1 任务内容](#1-任务内容)
- [2 评测数据](#2-评测数据)
- [3 评价标准](#3-评价标准)
- [4  Baseline](#4-Baseline)
- [5 评测赛程](#5-评测赛程)
- [6 奖项设置](#6-奖项设置)

## 1 任务内容

### 1.1 任务背景

2022年12月1日起，新出台的《反电信网络诈骗犯罪法》正式施行，表明了我国治理当前电信网络诈骗乱象的决心。诈骗案件分类问题是打击电信网路诈骗犯罪过程中的关键一环，根据不同的诈骗方式、手法等将其分类，一方面能够便于统计现状，有助于公安部门掌握当前电信网络诈骗案件的分布特点，进而能够对不同类别的诈骗案件作出针对性的预防、监管、制止、侦查等措施，另一方面也有助于在向群众进行反诈宣传时抓住重点、突出典型等。

### 1.2 任务简介

文本分类是自然语言处理领域的基础任务，面向电信网络诈骗领域的案件分类对智能化案件分析具有重要意义。本任务目的是对给定案件描述文本进行分类。案件文本包含对案件的整体描述（经过脱敏处理）。具体细节参考第2部分。

## 2 评测数据

### 2.1 数据简介

数据采集：案件文本内容为案情简述，即为受害人的笔录，由公安部门反诈大数据平台导出。
数据清洗：从反诈大数据平台共计导出 13 个类别的数据，去除了“其他类型诈骗”类别，因此最终采用 12 个类别。
脱敏处理：去除了案件文本中的姓名、出生日期、地址、涉案网址、各类社交账号以及银行卡号码等个人隐私或敏感信息。
分类依据：类别体系来源于反诈大数据平台的分类标准，主要依据受害人的法益及犯罪分子的手法进行分类，例如冒充淘宝客服谎称快递丢失的，分为冒充电商物流客服类；冒充公安、检察院、法院人员行骗的，分为冒充公检法及政府机关类；谎称可以帮助消除不良贷款记录的，分为虚假政信类等等。
类别数量：12 个类别。

### 2.2 数据样例

数据以json格式存储，每一条数据具有三个属性，分别为案件编号、案情描述、案件类别。样例如下：

```json
{
    "案件编号": 28043,
    "案情描述": "事主（女，20岁，汉族，大专文化程度，未婚，现住址：）报称2022年8月27日13时43分许在口被嫌疑人冒充快递客服以申请理赔为由诈骗3634元人民币。对方通过电话（）与事主联系，对方自称是中通快递客服称事主的快递物件丢失现需要进行理赔，事主同意后对方便让事主将资金转入对方所谓的“安全账号”内实施诈骗，事主通过网银的方式转账。事主使用的中国农业银行账号，嫌疑人信息：1、成都农村商业银行账号，收款人：；2、中国建设银行账号，收款人：。事主快递信息：中通快递，.现场勘查号：。",
    "案件类别": "冒充电商物流客服类"
},
{
    "案件编号": 49750,
    "案情描述": "2022 年 11 月 13 日 14 时 10 分 23 秒我滨河派出所接到 110 报警称在接到自称疾控中心诈骗电话，被骗元，接到报警民警赶到现场，经查，报警人，在辽宁省 17 号楼 162 家中，接到自称沈阳市疾控报警中心电话，对方称报警人去过，报警人否认后对方称把电话转接到哈尔滨市刑侦大队，自称刑侦大队的人说报警人涉及一桩洗钱的案件让报警人配合调查取证，调查取证期间让报警人把钱存到自己的银行卡中，并向报警人发送一个网址链接，在链接上进行操作，操作完后，对方在后台将报警人存在自己银行卡的钱全部转出，共转出五笔，共计元。",
    "案件类别": "冒充公检法及政府机关类"
},
{
    "案件编号": 78494,
    "案情描述": "2022 年 1 月 10 日 11 时至 18 时许，受害人在的家中，接到陌生电话：（对方号码：）对方自称是银保监会的工作人员，说受害人京东 APP 里有个金条借款要关闭，否则会影响征信。后对方就让受害人下载了“银视讯”的会议聊天软件，指导受害人如何操作，让受害人通过手机银行（受害人账户：1、交通银行；2、紫金农商银行；3、中国邮政储蓄银行：；4、中国民生银行：；）转账到对方指定账户：嫌疑人账户：1、中国农业银行；2、中国银行；3、中国银行；4、中国建设银行；5、中国银行；共计损失：元。案件编号：",
    "案件类别": "虚假征信类"
}
```

### 2.3 数据分布

提供数据共有12个类别，类别具体分布如下表所示。

| 类别名称                                 | 样本数量 |
| ---------------------------------------- | -------- |
| 刷单返利类                               | 35459    |
| 冒充电商物流客服类                       | 13772    |
| 虚假网络投资理财类                       | 11836    |
| 贷款、代办信用卡类                       | 11105    |
| 虚假征信类                               | 8464     |
| 虚假购物、服务类                         | 7058     |
| 冒充公检法及政府机关类                   | 4563     |
| 冒充领导、熟人类                         | 4407     |
| 网络游戏产品虚假交易类                   | 2155     |
| 网络婚恋、交友类（非虚假网络投资理财类） | 1654     |
| 冒充军警购物类                           | 1092     |
| 网黑案件                                 | 1197     |
| 总计                                     | 102762   |

训练集及测试集划分如下所示。

| 数据划分 | 样本数量 |
| -------- | -------- |
| 训练集   | 82210    |
| 测试集A  | 10276    |
| 测试集B  | 10276    |
| 总计     | 102762   |

本次评测任务计划仅采用训练集及测试集A以作评测。

## 3 评价标准

评测性能时，本任务主要采用宏平均F1值作为评价标准，即对每一类计算F1值，最后取算术平均值，其计算方式如下：

$$ Macro_{F1} = \frac{1}{n} \sum_{i=1}^{n} F1_{i} $$

其中 $F1_i$  为第i类的 $F1$ 值，n为类别数，在本任务中n取12。

## 4 Baseline

Baseline 主要采用 TextCNN、Bert 模型，具体介绍详见参考文献。

## 5 评测赛程

| 时间           | 事项                     |
| -------------- | ------------------------ |
| 4月10日~5月1日 | 开放报名                 |
| 4月20日        | 数据发布                 |
| 5月1日~5月10日 | 结果提交                 |
| 5月15日        | 公布评测结果             |
| 6月15日        | 截止提交评测任务技术报告 |

## 6 奖项设置

本届评测由中国中文信息学会为获奖队伍颁发荣誉证书，具体奖项设置如下：

- 一等奖：0-1名
- 二等奖：0-2名
- 三等奖：0-3名

## 7 参考文献

1. 中华人民共和国反电信网络诈骗法[J]. 中华人民共和国全国人民代表大会常务委员会公报, 2022, No.359(05): 709-716.
2. 60 种典型电信诈骗方式[J]. 中国防伪报道, 2019, No.230(11): 37-41.
3.  刘玲玲, 毕梦瀛, 沈小晓. 多国出台措施打击电信网络诈骗[N]. 人民日报, 2023-01-05(017). DOI: 10.28655/n.cnki.nrmrb.2023.000168.
4. 张维炜. 密织反诈“防护网” 压实“守门人”责任——反电信网络诈骗法正式实施[J].中国人大, 2022, No.563(23): 33-34.
5. 王洁. 电信网络诈骗犯罪的独特属性与治理路径[J]. 中国人民公安大学学报(社会科学版), 2019, 35(04): 1-10.
6. YOON Kim.Convolutional Neural Networks for Sentence Classification[C]. EMNLP, 2014: 1746-1751.
7. DEVLIN J, CHANG M W, LEE K, et al. BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding[J]. arXiv:1810.04805v1, 2018.