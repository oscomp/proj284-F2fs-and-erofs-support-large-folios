# proj284-F2fs-and-erofs-support-large-folios
## f2fs和erofs支持large folios



## 项目描述

目前Linux mainline的page cache通用层针对文件页支持large folios，并有部分文件系统对通用层提供了支撑。这类文件系统会调用如下API向上宣称支持：mapping_set_large_folios(inode->i_mapping)；

目前支持的文件系统有：xfs、afs、非压缩的erofs，但是手机常用文件系统不支持large folios。

 本课题有如下两个分课题：

1. 针对压缩的erofs文件支持large folios **（难度中）**

由于erofs是只读的文件系统，所以当page cache层传递一个large folio给erofs的时候，erofs应该能够读出这个large folio。

2. 针对f2fs文件系统支持large folios **（难度高）**

f2fs文件系统是可读写的，而且内含garbage collect(GC)，因此需要与 pagecache传递的large folios有更多的互动。gc也需要识别理解large folios。



## 预期目标

- erofs压缩文件可变large folios；
- f2fs可变large folios。

参赛团队可只选1或者2，或者二者皆选。

1的难度中，2的难度高。



OPPO在手机上采用以上两个技术实现：

1. 安兔兔等跑分软件提分；

2. 文件页的LRU维护成本、内存回收成本等显著降低，类小白、整机性能提升。

## 特征

主要是开发功能，只需要qemu验证和调试内核即可，不需要真实硬件电路板。

主要考察：

·  通过阅读内核源代码，社区LKML邮件列表自主学习的能力；

·  在通过内核源码、LKML自主学习后，结合page cache和文件系统的代码，自主修改文件系统，进行功能适配的能力。



## 已有参考资料

- ·  Linux主线代码；

- qemu虚拟arm64主机进行调试。

  

## 赛题分类

文件系统

## 参赛要求

以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生或研究生；

允许学生参加大赛的多个不同题目，最终自己选择一个题目参与评奖；

请遵循“2025全国大学生操作系统比赛”的章程和技术方案要求。



## 难度

中等/高等



## License

GPL v2.



## 所属赛道

2025全国大学生操作系统比赛的“OS功能挑战”赛道

## 项目导师

- 姓名：宋宝华（OPPO顾问）
- 单位：OPPO
- email：[v-songbaohua@oppo.com](mailto:v-songbaohua@oppo.com)
