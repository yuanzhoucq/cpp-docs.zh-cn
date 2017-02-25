---
title: "tiled_index 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tiled_index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tiled_index 类"
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# tiled_index 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供 [tiled\_extent](../../../parallel/amp/reference/tiled-extent-class.md) 对象的索引。  该类具有访问相对于本地平铺原点和相对于全局原点的元素的属性。  有关平铺空间的更多信息，请参阅 [使用平铺](../../../parallel/amp/using-tiles.md)。  
  
## 语法  
  
```  
template <  
   int _Dim0,  
   int _Dim1 = 0,  
   int _Dim2 = 0  
>  
class tiled_index : public _Tiled_index_base<3>;  
  
template <  
   int _Dim0,  
   int _Dim1  
>  
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;  
  
template <  
   int _Dim0  
>  
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;  
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
|[tiled\_index::tiled\_index 构造函数](../Topic/tiled_index::tiled_index%20Constructor.md)|初始化 `tile_index` 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[tiled\_index::get\_tile\_extent 方法](../Topic/tiled_index::get_tile_extent%20Method.md)|返回具有 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 模板参数 `_Dim0`、`_Dim1` 和 `_Dim2` 值的[范围](../../../parallel/amp/reference/extent-class-cpp-amp.md)对象。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[tiled\_index::barrier 常量](../Topic/tiled_index::barrier%20Constant.md)|存储一个表示当前线程平铺中的一个障碍的 [tile\_barrier](../../../parallel/amp/reference/tile-barrier-class.md) 对象。|  
|||  
|[tiled\_index::global 常量](../Topic/tiled_index::global%20Constant.md)|存储一个表示[网格](http://msdn.microsoft.com/zh-cn/f7d1b6a6-586c-4345-b09a-bfc26c492cb0)对象全局索引的 1、2 或 3 级[索引](../../../parallel/amp/reference/index-class.md)对象。|  
|[tiled\_index::local 常量](../Topic/tiled_index::local%20Constant.md)|存储一个表示 [tiled\_extent](../../../parallel/amp/reference/tiled-extent-class.md) 对象当前平铺相关索引的 1、2 或 3 级 `index` 对象。|  
|[tiled\_index::rank 常量](../Topic/tiled_index::rank%20Constant.md)|存储 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 对象的秩。|  
|[tiled\_index::tile 常量](../Topic/tiled_index::tile%20Constant.md)|存储一个表示 `tiled_extent` 对象当前平铺坐标的 1、2 或 3 级 `index` 对象。|  
|[tiled\_index::tile\_dim0 常量](../Topic/tiled_index::tile_dim0%20Constant.md)|存储最高有效位维的长度。|  
|[tiled\_index::tile\_dim1 常量](../Topic/tiled_index::tile_dim1%20Constant.md)|存储接近最高有效位维的长度。|  
|[tiled\_index::tile\_dim2 常量](../Topic/tiled_index::tile_dim2%20Constant.md)|存储最低有效位维的长度。|  
|[tiled\_index::tile\_origin 常量](../Topic/tiled_index::tile_origin%20Constant.md)|存储一个表示 `tiled_extent` 对象当前平铺原始全局坐标的 1、2 或 3 级 `index` 对象。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[tiled\_index::tile\_extent 数据成员](../Topic/tiled_index::tile_extent%20Data%20Member.md)|获取具有 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 模板参数 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 模板参数 `_Dim0`、`_Dim1` 和 `_Dim2` 的值的[范围](../../../parallel/amp/reference/extent-class-cpp-amp.md)对象。|  
  
## 继承层次结构  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## 要求  
 **标头：**amp.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)