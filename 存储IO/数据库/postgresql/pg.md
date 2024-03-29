pg开发

教科书级别的数据库

PG的开源许可是类BSD许可。可以随意分发、闭源或者开源。

# 1 初识PG

## 1.1 pg的生态

**历史**

可以追溯到1973

中文官方文档：

http://www.postgres.cn/docs/10/history.html

pg wiki：

https://zh.wikipedia.org/wiki/PostgreSQL

pg roadmap：

https://www.postgresql.org/developer/roadmap/

postgresql commitfest：

https://commitfest.postgresql.org/



**PostgreSQL 社区分析 - 为什么PostgreSQL社区几乎不可能被任何一个商业公司、国家所控制？**

https://github.com/digoal/blog/blob/master/201906/20190608_02.md



**社区**

2011年成立

技术生态圈：

内核、用户、培训机构、厂商、服务商、软件开发商、高校形成`业务与利益双向驱动`的良性发展生态圈

社区组织架构：

- 轮值主席
- 常委（分管社区官网、官微、宣传、志愿者、财务）
- 分会会长
- pg大学虚拟小组
- 核心成员（阿里、腾讯、中兴、武汉大学。。。）

社区规模：

bbs、微信、QQ、微博、钉钉

社区运作：

- 公益活动：pg分会、区域会议、社区培训、技术直播、在线答疑
- 盈利模式探索
  - 流量价值，企业长期赞助
  - 社区淘宝店，售卖pg社区书籍、文化衫、笔记本等
  - 盈利回馈社区，支持社区运作



**pg特性**

![pg定位_企业型数据库](./images/pg定位_企业型数据库.png)







**pg常见数据库部署架构**

- 单机

- 基于共享存储的HA

- 基于流复制的HA

- 读写分离

- 单元化

- 多主部署（`multi-master`）
  - xDB：https://github.com/digoal/blog/blob/master/201902/20190203_01.md
  - https://github.com/digoal/blog/blob/master/201811/20181119_01.md

- 基于物理流复制的强一致多副本（兼具可用性、可靠性）
- 级联复制
- Sharding
  - https://github.com/digoal/blog/blob/master/201808/20180824_02.md



![pg常见部署架构](./images/pg常见部署架构-1.png)



![image-20240328224758155](./images/pg常见部署架构-2.png)



**pg备份**

- 全量+归档增量备份
- 全量+块级增量备份
  - https://github.com/digoal/blog/blob/master/201608/20160826_01.md
- 快照+归档增量备份
  - https://github.com/digoal/blog/blob/master/201608/20160823_05.md
- 时间点恢复
  - https://github.com/digoal/blog/blob/master/201901/20190120_03.md
- 容灾
  - https://github.com/digoal/blog/blob/master/201901/20190128_02.md
- 链路加密
- 数据存储加密
- 数据类型加密
- 数据库ACL
- SQL防火墙
- 外部数据库（冷热分离）
- 跨库访问
- 同构、异构增量同步

![pg备份-1](./images/pg备份-1.png)



![pg还原-1](./images/pg还原-1.png)

![pg复制-1](./images/pg复制-1.png)





**客户群**

xxxx



**应用场景**

- 企业级核心应用，代替oracle

- IoT

- GIS地理信息，时空场景

- 实时BI（实时任意维度数据搜索、透视、复杂分析）

- 混合负载业务（既有AP又有TP）

- 图像搜索

- 向量相似查询

- SQL流计算

- 搜索（全文检索、模糊检索、任意字段组合检索、相似搜索、正则搜索）

- 冷热数据分离（oss_fdw、file_fdw。。。）
  - https://www.postgresql.org/docs/current/postgres-fdw.html
  - https://wiki.postgresql.org/wiki/Foreign_data_wrappers

- 沙箱
  - https://github.com/digoal/blog/blob/master/201805/20180524_02.md

- 如来神掌
  - https://github.com/digoal/blog/blob/master/201706/20170601_02.md



**生态**

pg系数据库：

https://wiki.postgresql.org/wiki/PostgreSQL_derived_databases



![pg多模-1](./images/pg多模-1.png)





**pg和其他商用数据库的差异化**

xxxx







**pg学习资料**

文档：

https://github.com/digoal/blog/blob/master/README.md

Oracle DBA PG学习手册：

https://github.com/digoal/blog/blob/master/201804/20180425_01.md

如来神掌，pg大量应用场景实践：

https://github.com/digoal/blog/blob/master/201706/20170601_02.md

原理、开发、管理、实践：

https://github.com/digoal/blog/blob/master/201801/20180121_01.md

沙箱：

https://github.com/digoal/blog/blob/master/201805/20180524_02.md















**交流圈子**

xxxx

 **架构独特性**

PG采用了开放接口的设计：

- type，operator，index
- storage，language，fdw
- custom，scan，sample，hook等

基于PG开发接口扩展的产品或插件：

- 基于PG的图数据库agensgraph，edgedb
- 流数据库pipelinedb
- GIS PostGIS，pgrouting，pgpointcloud
- 时序数据库 timescaledb
- 推荐数据库 recdb
- 搜索引擎 Yahoo! Everest
- MPP greenplum，redshift，asterdata
- 机器学习 madlib
- 图像识别 imgsmlr
- 分词 zhparser，pg_jieba
- 分布式数据库 citus，pg-xI，华为Gauss，antdb
- Oracle兼容 edb
- 文档数据库 torodb



pg插件仓库：

https://pgxn.org/

Gis插件：

https://postgis.net/



**技术趋势**

1、pg是多模数据库，因为它的开放性，可以随意扩展。例如前面提到的诸多插件，使得PG是目前最强大的多模数据库。

2、内置并行计算（36种并行计算场景（几乎涵盖所有ap sql），平均提速20倍以上）。

3、支持存储引擎扩展（12，zheap，zedstore）。

4、对芯片友好，如ARM芯片的支持。

以上4点满足市场的既要又要还要的需求：

既要SQL通用性，又要NOSQL扩展性，还要多模开发便捷性。

既要OLTP又要OLAP。



PG OLAP能力

PostgreSQL 11 并行计算使用场景、性能提升倍数：

https://github.com/digoal/blog/blob/master/201903/20190318_05.md





知识图谱：

![pg知识图谱](./images/pg知识图谱.png)



参考：

https://github.com/digoal/blog

https://github.com/digoal/blog/blob/master/201901/20190105_01.md
