# CCL 2023 电信网络诈骗案件分类评测

##### 组织者：孙承杰 sunchengjie@hit.edu.cn

##### 负责人：纪杰 jijie@insun.hit.edu.cn

##### 联系人：纪杰 jijie@insun.hit.edu.cn

## 目录

- [1 任务内容](#1-任务内容)
- [2 评测数据](#2-评测数据)
- [3 评价标准](#3-评价标准)
- [4 提交方式](#4-提交方式)
- [5 评测赛程](#5-评测赛程)
- [6 奖项设置](#6-奖项设置)

## 1 任务内容

### 1.1 任务背景

2022年12月1日起，新出台的《反电信网络诈骗犯罪法》正式施行，表明了我国治理当前电信网络诈骗乱象的决心。诈骗案件分类问题是打击电信网路诈骗犯罪过程中的关键一环，根据不同的诈骗方式、手法等将其分类，一方面能够便于统计现状，有助于公安部门掌握当前电信网络诈骗案件的分布特点，进而能够对不同类别的诈骗案件作出针对性的预防、监管、制止、侦查等措施，另一方面也有助于在向群众进行反诈宣传时抓住重点、突出典型等。

### 1.2 任务简介

文本分类是自然语言处理领域的基础任务，面向电信网络诈骗领域的案件分类对智能化案件分析具有重要意义。本任务目的是对给定案件描述文本进行分类。案件文本包含对案件的整体描述（经过脱敏处理）。具体细节参考第2部分。

## 2 评测数据

### 2.1 数据样例

数据以json格式存储，每一条数据具有三个属性，分别为案件编号、案情描述、案件类别。样例如下：

```json
{
    "案件编号": 28043,
    "案情描述": "事主（女，20岁，汉族，大专文化程度，未婚，现住址：）报称2022年8月27日13时43分许在口被嫌疑人冒充快递客服以申请理赔为由诈骗3634元人民币。对方通过电话（）与事主联系，对方自称是中通快递客服称事主的快递物件丢失现需要进行理赔，事主同意后对方便让事主将资金转入对方所谓的“安全账号”内实施诈骗，事主通过网银的方式转账。事主使用的中国农业银行账号，嫌疑人信息：1、成都农村商业银行账号，收款人：；2、中国建设银行账号，收款人：。事主快递信息：中通快递，.现场勘查号：。",
    "案件类别": "冒充电商物流客服类"
}

```

### 2.2 数据分布

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

## 4 提交方式

暂无

## 5 评测赛程

| 时间            | 事项                     |
| --------------- | ------------------------ |
| 4月10日~5月10日 | 开放报名                 |
| 5月1日          | 数据发布                 |
| 5月10日~5月20日 | 结果提交                 |
| 5月25日         | 公布评测结果             |
| 6月25日         | 截止提交评测任务技术报告 |

## 6 奖项设置

本届评测由中国中文信息学会为获奖队伍颁发荣誉证书，具体奖项设置如下：

- 一等奖：0-1名
- 二等奖：0-2名
- 三等奖：0-3名