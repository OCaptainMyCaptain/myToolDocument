# <center>**关于OA异常重启后“非合同用印”库长时间一致性检查导致不能使用的问题的初步处理方案**</center>
## **1. 问题简述**
    OA系统长期存在异常重启的问题，早年缺乏监控机制，也没有出现影响使用的现象，故一直没有发现。现今，由于使用年限增加，个别流程库大小已接近domino 8版本下文件最大大小限制，每次异常重启后，都需要花费较长时间用于流程库的一致性检查，特别是“非合同用印”流程库，一致性检查所需时间大约为两个小时，期间不能使用，严重影响了正常工作。
## **2. 问题排查**
    通过对OA异常重启前后的日志文件的分析，初步认为该问题如下：
    （1）人力流程库的某个代理异常导致OA异常重启
    （2）非合同用印流程库过大，导致一致性检查时间过长  
    针对以上两个问题，目前已经通过增加配置，打印更多日志的方式，尝试定位问题代码，但实际效果微乎其微，近两次异常重启后并未从日志中找到更有价值的内容。
## **3. 其他方案**
    （1）购买少量授权
        OA异常重启后，domino有收集底层的日志形成文件，但该文件需domino开发商（IBM）提供支持才能解读，所以可以通过购买少量（烦请确认所需购买量，及最终价格）授权的形式获取IBM（还是HCL？）的技术支持。
    （2）增加代理进行监控
        通过新增定时代理，在每天晚上系统负载较小的时间，收集当天流程库运行状况，如数据增量、库当前大小等（补充一下还有哪些东西是可以收集的），并形成分析报告，通过进一步分析，帮助定位程序异常代码，排查问题。
    （3）升级domino版本
        目前，OA所依赖的domino版本为8.5.3，存在库最大大小限制（64G），但domino在10及以上版本已取消了改限制，所以可以考虑升级domino版本解决流程库太大的问题，但domino升级存在重大风险，请出具具体的升级方案以及回退方案。
    （4）对大库进行定期拆库
        到以上方案，耗时都比较久，无法在短期内解决或缓解OA异常重启后“非合同用印”库长时间一致性检查导致不能使用的问题，可通过拆库的方式，先减小大库的容量，缩减一致性检查的时间，保证在问题得到彻底解决之前，OA异常重启后不会长时间影响正常工作。
## **4. OA升级**
    现行的OA系统使用年限已近10年，当初的设计、架构已经逐渐不再适应今天的需求，包括流程引擎落后，不能设计复杂的流程以满足现实需要、浏览器兼容性差、可扩展性差等诸多问题。无论是升级新版的domino架构，还是更换其他OA厂商，都是值得考虑的方案。