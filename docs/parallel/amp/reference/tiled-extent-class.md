---
title: "tiled_extent 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tiled_extent"
dev_langs: 
  - "C++"
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# tiled_extent 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`tiled_extent` 对象是到一维到三维的 `extent` 对象，该对象将区域空间细分成一维、二维或三维平铺。  
  
## 语法  
  
```  
template <  
   int _Dim0,  
   int _Dim1,  
   int _Dim2  
>  
class tiled_extent : public Concurrency::extent<3>;  
  
template <  
   int _Dim0,  
   int _Dim1  
>  
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;  
  
template <  
   int _Dim0  
>  
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;  
```  
  
#### 参数  
 `_Dim0`  
 最高有效位维的长度。  
  
 `_Dim1`  
 接近最高有效维的长度。  
  
 `_Dim2`  
 最低有效位维的长度。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[tiled\_extent::tiled\_extent 构造函数](../Topic/tiled_extent::tiled_extent%20Constructor.md)|初始化 `tiled_extent` 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[tiled\_extent::get\_tile\_extent 方法](../Topic/tiled_extent::get_tile_extent%20Method.md)|返回捕捉 `tiled_extent` 模板参数 `_Dim0`、`_Dim1` 和 `_Dim2` 的值的 `extent` 对象。|  
|[tiled\_extent::pad 方法](../Topic/tiled_extent::pad%20Method.md)|返回范围通过图标维度将范围平均变大的新 `tiled_extent` 对象。|  
|[tiled\_extent::truncate 方法](../Topic/tiled_extent::truncate%20Method.md)|返回范围通过图标维度将范围平均变小的新 `tiled_extent` 对象。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[tiled\_extent::operator\= 运算符](../Topic/tiled_extent::operator=%20Operator.md)|将指定的 `tiled_index` 对象的内容复制到此对象中。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[tiled\_extent::tile\_dim0 常量](../Topic/tiled_extent::tile_dim0%20Constant.md)|存储最高有效位维的长度。|  
|[tiled\_extent::tile\_dim1 常量](../Topic/tiled_extent::tile_dim1%20Constant.md)|存储接近最高有效位维的长度。|  
|[tiled\_extent::tile\_dim2 常量](../Topic/tiled_extent::tile_dim2%20Constant.md)|存储最低有效位维的长度。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[tiled\_extent::tile\_extent 数据成员](../Topic/tiled_extent::tile_extent%20Data%20Member.md)|获取捕获 `tiled_extent` 模板参数 `_Dim0`、`_Dim1` 和 `_Dim2` 的值的 `extent` 对象。|  
  
## 继承层次结构  
 `extent`  
  
 `tiled_extent`  
  
## 要求  
 **标头：**amp.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)