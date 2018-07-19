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

- 提供的高程数据范围是83°N - 83°S的全球部分，按照1° * 1°的瓦片大小划分，每个瓦片标注经纬度位置，共有22702块。

- 每个瓦片文件的格式是GeoTIFF，图片长宽是3601*3601，对应经纬度1° * 1°范围，每个像素约合一角秒。

- 像素使用signed 16-bit描述，单位是米，高度基准以WGS84 / EGM96为参考系。-9999表示空值。
