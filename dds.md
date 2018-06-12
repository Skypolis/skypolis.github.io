# DDS历史
2001年Real-Time Innovations和法国Thales Group创建了DDS规范，2004年被OMG认证为V1.0版本，2015年发展到V1.4版

# DDS结构
DDS包括两层协议

* data-centric publish-subscribe (DCPS)
* higher data local reconstruction layer (DLRL)，可选，1.4版本中被移到其他规范

DDS具有多个相关协议
* Real-time Publish-Subscribe Wire Protocol DDS Interoperability Wire Protocol Specification
* DDS for Lightweight CCM
* Extensible and Dynamic Topic Types for DDS (DDS-XTypes)

模型
* DDS在nodes之间实现data、events、commands的发布订阅
* 发送node生成topic，然后发布sample，DDS负责将sample传递给订阅该topic的node
* DDS的发布订阅模型事实上屏蔽了底层的复杂网络编程，实现了程序之间的通信解耦

互操作
* 2009年Real-Time Innovations, Inc., PrismTech and Twin Oaks三家开发商实现了各自产品之间的互操作
* 2013年又有六家开发商实现了互操作OCI(OpenDDS),  ETRI , IBM, Kongsberg, MilSoft, RemedyIT    

# DDS产品

1. OCI （OpenDDS）
>* C++开发，github开源
>* 支持C++和Java，基于ACE和TAO，支持V1.4规范
>* 支持TCP、UDP、Multicast，支持基于UDP的RTPS（V2.2规范）

2. PrismTech （Vortex OpenSlice）
>* 有商业版和社区版，社区版github开源
>* 支持OMG DDS rev1.4 (DCPS profiles) 和 OMG-DDSI / RTPS v2.2 interoperable wire-protocol standards
>* 支持C、C++、C#、Java，支持scala、python
>* OMG DDSI-rev2.2支持TCP
>* 支持RMI、Streams、Google Protocol Buffers (GPB)、MATLAB and Simulink

3. Real-Time Inovations （Connext DDS）
>* 只有商业版，Connext DDS 5.3版本具有30天试用期
>* 支持C, C++, C#/.NET, Java, Ada、Lua、JavaScript(node.js)、Python、LabVIEW、MATLAB、Simulink
>* 千兆网延迟不超过50ms
>* 支持DDS API 1.4和DDS Wire Protocol (RTPS) 2.2 
