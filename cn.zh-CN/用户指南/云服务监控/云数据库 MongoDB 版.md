# 云数据库 MongoDB 版 {#concept_bwg_gx4_ydb .concept}

云监控通过监控云数据库 MongoDB 版服务实例的 CPU 使用率、内存使用率等多个监控项，帮助用户监测实例的运行状态，并支持用户对监控项设置报警规则。用户购买 MongoDB 服务后，云监控会自动对上述监控项收集数据。

## 监控服务 {#section_xjm_3x4_ydb .section}

-   监控项

    |监控项|含义|维度|单位|最小监控粒度|
    |:--|:-|:-|:-|:-----|
    |CPU使用率|实例的CPU使用率|用户维度、实例维度、主备维度|百分比|5分钟|
    |内存使用率|实例的内存使用率|用户维度、实例维度、主备维度|百分比|5分钟|
    |磁盘使用率|实例的磁盘使用率|用户维度、实例维度、主备维度|百分比|5分钟|
    |IOPS使用率|实例的IOPS使用率|用户维度、实例维度、主备维度|百分比|5分钟|
    |连接数使用率|连接数是指应用程序可以连接到MongoDB实例的数量。连接数使用率即已经使用的连接数百分率|用户维度、实例维度、主备维度|百分比|5分钟|
    |平均每秒SQL查询数|MongoDB实例的平均每秒SQL查询数|用户维度、实例维度、主备维度|个数|5分钟|
    |连接数使用量|当前应用程序连接到MongoDB实例的数量|用户维度、实例维度、主备维度|个数|5分钟|
    |实例占用磁盘空间量|实例实际使用的磁盘空间总量|用户维度、实例维度、主备维度|字节|5分钟|
    |数据占用磁盘空间量|数据占用的磁盘空间容量|用户维度、实例维度、主备维度|字节|5分钟|
    |日志占用磁盘空间量|日志占用的磁盘空间容量|用户维度、实例维度、主备维度|字节|5分钟|
    |内网入流量|实例的网络流入流量|用户维度、实例维度、主备维度|字节|5分钟|
    |内网出流量|实例的网络流出流量|用户维度、实例维度、主备维度|字节|5分钟|
    |请求数|发送到服务端的请求总量|用户维度、实例维度、主备维度|个数|5分钟|
    |Insert操作次数|从MongoDB实例最近一次启动到现在累计接收到的insert命令的次数|用户维度、实例维度、主备维度|个数|5分钟|
    |Query操作次数|从MongoDB实例最近一次启动到现在累计接收到的query命令的次数|用户维度、实例维度、主备维度|字节|5分钟|
    |Update操作次数|从MongoDB实例最近一次启动到现在累计接收到的update命令的次数|用户维度、实例维度、主备维度|次数|5分钟|
    |Delete操作次数|从MongoDB实例最近一次启动到现在累计执行delete的操作次数|用户维度、实例维度、主备维度|次数|5分钟|
    |Getmore操作次数|从MongoDB实例最近一次启动到现在累计执行getmore的操作次数|用户维度、实例维度、主备维度|次数|5分钟|
    |Command操作次数|从MongoDB实例最近一次启动到现在向数据库发出的command的累计次数|用户维度、实例维度、主备维度|次数|5分钟|
    |实例故障|事件类型指标，可设置报警规则|-|-|-|

    **说明：** 

    -   监控数据最多保存31天。

    -   用户最多可连续查看14天的监控数据。


-   查看监控数据
    1.  登录[云监控控制台](http://cms.console.aliyun.com/#/groups/)。
    2.  进入**云服务监控**下的**云数据库 MongoDB 版**实例列表。
    3.  点击实例名称或**操作**中的**监控图表**即可进入实例监控详情页面，查看各项指标。
    4.  点击页面上方的**时间范围**快速选择按钮或精确选择功能，监控数据最长支持查看连续 14 天的监控数据。
    5.  点击监控图右上角的放大按钮，可查看监控大图。

## 报警服务 {#section_cpf_3qp_ydb .section}

-   参数说明
    -   监控项：云数据库 MongoDB 版提供的监控指标。
    -   统计周期：报警系统会按照这个周期检查您对应的监控数据是否超过了报警阈值。例如设置内存使用率报警规则的统计周期为1分钟，则每间隔1分钟会检查一次内存使用率是否超过了阈值。
    -   统计方法：统计方法指对超出阈值范围的设置。统计方法中可以设置平均值、最大值、最小值、求和值。
        -   平均值：统计周期内监控数据的平均值。统计结果是15分钟内采集的所有监控数据的平均值，当这个平均值大于80%时，才算超过阈值。
        -   最大值：统计周期内监控数据的最大值。统计周期内采集的监控数据中，最大值超过80%，即为超过阈值。
        -   最小值：统计周期内监控数据的最小值。统计周期内采集的监控数据中，最小值超过80%，即为超过阈值。
        -   求和值：统计周期内监控数据的总和。对统计周期内采集的监控数据进行求和，求和后的结果超过80%即为超过阈值。流量类指标需要用到此类统计方法。
    -   连续次数：指连续几个统计周期监控项的值持续超过阈值后触发报警。

        例如：设置CPU使用率超过80%报警，统计周期为5分钟，连续3次超过阈值后报警，则第一次探测CPU使用率超过80%时，不会发出报警通知。5分钟后第二次探测CPU使用率超过80%，也不会发出报警。第三次探测仍然超过80%时，才会发出报警通知。即从实际数据第一次超过阈值到最终发出报警规则，最少需要消耗的时间为统计周期\(连续探测次数-1\)=5\(3-1\)=10分钟。

-   设置单条报警规则
    1.  登录[云监控控制台](http://cms.console.aliyun.com/#/groups/)。
    2.  进入**云服务监控**下的**云数据库 MongoDB 版**实例列表。
    3.  单击实例名称或**操作**中的**监控图表**，进入实例的监控详情页面。
    4.  点击监控图右上角的铃铛按钮，可对该实例对应的监控项设置报警规则。

-   设置批量报警规则
    1.  登录[云监控控制台](http://cms.console.aliyun.com/#/groups/)。
    2.  进入**云服务监控**下的**云数据库 MongoDB 版**实例列表。
    3.  实例列表页面选中所需实例后，在页面下方点击**设置报警规则**，即可批量添加报警规则。

