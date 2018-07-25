---
layout: post
title: "通过GIS数据在Unity中创建3D地形"
date: 2018-07-19
description: "Build terrain in Unity by GIS data"
tag: blog
---   

# 高程数据源ASTER GDEM

ASTER GDEM数据由日本METI和美国NASA联合测量处理后提供，有V1和V2两个版本。在中科院网站可下载到。

V1版本 http://www.gscloud.cn/sources/dataset_desc/310?cdataid=302&pdataid=10&datatype=gdem_utm

V2版本 http://www.gscloud.cn/sources/dataset_desc/421?cdataid=302&pdataid=10&datatype=gdem_utm2

在下载到的压缩包里可以找到readme.pdf解释具体格式。主要内容抽取如下：

- 提供的高程数据范围是83°N - 83°S的全球部分，按照1° * 1°的瓦片大小划分，每个瓦片标注经纬度位置，共有22702块。每张图像大小是24.7M。

- 每个瓦片文件的格式是GeoTIFF，图片长宽是3601*3601，对应经纬度1° * 1°范围，每个像素约合一角秒。

- 像素使用signed 16-bit描述，单位是米，高度基准以WGS84 / EGM96为参考系。-9999表示空值。

- GDEM 2 has an overall accuracy of around 17-m at the 95% confidence level, and a horizontal resolution on the order of 75-m

# Unity中的高程格式

Unity中的terrain采用RAW文件格式进行导入导出

- 没有header，根据Unity中的Height Resolution设置的像素数读取像素，必须是2的整次幂+1

- 与ASTER GDEM不同，像素灰度值代表的是相对高度。像素值相对于8位的256和16位的65536比例是该点高度相对于Terrain Height的百分比。

- 可以选择windows和mac两种字节序

- Unity中的X轴正向 = raw图像右，Z轴正向 = raw图像下。所以从Y轴负方向看时导入需要选择Flip Vertical。

- Unity的Terrain Width/Length上限是100000，Terrain Height上限是10000

# 从ASTER GDEM到Unity的高程格式转换

- 使用Global Mapper进行转换，原始的多张ASTGTM2数据tif文件可以在GlobalMapper中自动拼成大地形

- 选择Export→Export Elevation Grid→RAW，选择16位精度，v17可以选择signed short或unsigned short

- 在导出时通过Sampling可以进行重采样，对高程进行插值，可以选择不同的插值算法

- 通过Gridding设置切块，可以设置多块地形的自动切分和命名

- 可以对导出的raw文件进行自定义处理，调整异常点或海拔高度

# 卫片处理

- 从Google Map上下载指定区域的卫片作为原始数据

- Unity中的纹理必须是正方形，分辨率是2的整次幂，因此需要通过Photoshop或Global Mapper处理成此格式
