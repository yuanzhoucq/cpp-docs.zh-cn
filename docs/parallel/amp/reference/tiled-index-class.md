---
title: "tiled_index 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::tiled_index
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 2c10721f40bd1c90a196ba82655482f35a8e10d8
ms.lasthandoff: 02/24/2017

---
# <a name="tiledindex-class"></a>tiled_index 类
提供到索引[tiled_extent](tiled-extent-class.md)对象。 此类的属性来访问元素相对于本地磁贴原点和相对于全局源。 有关平铺空间的详细信息，请参阅[使用磁贴](../../../parallel/amp/using-tiles.md)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `_Dim0`  
 最重要的维的长度。  
  
 `_Dim1`  
 下一步最不重要的维度的长度。  
  
 `_Dim2`  
 最不重要的维的长度。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[tiled_index 构造函数](#ctor)|初始化 `tile_index` 类的新实例。|  

  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_tile_extent 方法](#tiled_index__get_tile_extent)|返回[扩展盘区](extent-class.md)对象，它具有的值`tiled_index`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。|  


  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[barrier 常量](#tiled_index__barrier)|存储[tile_barrier](tile-barrier-class.md)对象，表示当前线程的 tile 中的障碍。|  
|||  
|[全局常量](#tiled_index__global)|存储[索引](index-class.md)对象中的级别 1、 2 或 3，表示全局索引[网格](http://msdn.microsoft.com/en-us/f7d1b6a6-586c-4345-b09a-bfc26c492cb0)对象。|  
|[local 常量](#tiled_index__local)|存储`index`对象当前 tile 中的索引，级别 1、 2 或 3，表示相对[tiled_extent](tiled-extent-class.md)对象。|  
|[rank 常量](#tiled_index__rank)|将存储的排名`tiled_index`对象。|  
|[tile 常量](#tiled_index__tile)|存储`index`对象的秩为 1、 2 或 3 表示当前 tile 的坐标`tiled_extent`对象。|  
|[tile_dim0 常量](#tiled_index__tile_dim0)|将存储的最重要的维度的长度。|  
|[tile_dim1 常量](#tiled_index__tile_dim1)|将存储的下一步最不重要的维度的长度。|  
|[tile_dim2 常量](#tiled_index__tile_dim2)|存储最不重要的维度的长度。|  
|[tile_origin 常量](#tiled_index__tile_origin)|存储`index`对象在当前 tile 的原点的级别 1、 2 或 3，表示全局坐标`tiled_extent`对象。|  

  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[tile_extent 数据成员](#tile_extent)|获取[扩展盘区](extent-class.md)对象，它具有的值`tiled_index`模板参数`tiled_index`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。|  

  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  


## <a name="a-nametiledindexctora--tiledindex-constructor"></a><a name="tiled_index__ctor"></a>tiled_index 构造函数  
初始化 `tiled_index` 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
tiled_index(  
    const index<rank>& _Global,  
    const index<rank>& _Local,  
    const index<rank>& _Tile,  
    const index<rank>& _Tile_origin,  
    const tile_barrier& _Barrier ) restrict(amp,cpu);  
  
tiled_index(  
    const tiled_index& _Other ) restrict(amp,cpu);  
```  
  
#### <a name="parameters"></a>参数  
 `_Global`  
 全局[索引](index-class.md)构造`tiled_index`。  
  
 `_Local`  
 本地[索引](index-class.md)的构造`tiled_index`  
  
 `_Tile`  
 该图块[索引](index-class.md)的构造`tiled_index`  
  
 `_Tile_origin`  
 磁贴原点[索引](index-class.md)的构造`tiled_index`  
  
 `_Barrier`  
 [Tile_barrier](tile-barrier-class.md)所构造的对象`tiled_index`。  
  
 `_Other`  
 `tile_index`对象要复制到所构造`tiled_index`。  
  
## <a name="overloads"></a>Overloads  
  
|||  
|-|-|  
|名称|描述|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|新实例初始化`tile_index`类从索引的全局坐标中的磁贴和磁贴的本地坐标中的相对位置。 `_Global`和`_Tile_origin`计算参数。|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|新实例初始化`tile_index`通过复制指定的类`tiled_index`对象。|  


## <a name="a-nametiledindexgettileextenta--gettileextent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent
返回[扩展盘区](extent-class.md)对象，它具有的值`tiled_index`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。  
  
## <a name="syntax"></a>语法  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>返回值  
 一个 `extent` 对象，具有 `tiled_index` 模板参数 `_Dim0`、`_Dim1` 和 `_Dim2` 的值。  

## <a name="a-nametiledindexbarriera--barrier"></a><a name="tiled_index__barrier"></a>屏障   
存储[tile_barrier](tile-barrier-class.md)对象，表示当前线程的 tile 中的障碍。  
  
## <a name="syntax"></a>语法  
  
```  
const tile_barrier barrier;  
```  

## <a name="a-nametiledindexglobala--global"></a><a name="tiled_index__global"></a>全局   
存储[索引](index-class.md)秩为 1、 2 或 3，表示对象的全局索引的对象。  
  
## <a name="syntax"></a>语法  
  
```  
const index<rank> global;  
```  
  
## <a name="a-nametiledindexlocala--local"></a><a name="tiled_index__local"></a>本地   
存储[索引](index-class.md)对象当前 tile 中的索引，级别 1、 2 或 3，表示相对[tiled_extent](tiled-extent-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
const index<rank> local;  
```  
  
## <a name="a-nametiledindexranka--rank"></a><a name="tiled_index__rank"></a>排名   
将存储的排名`tiled_index`对象。  
  
## <a name="syntax"></a>语法  
  
```  
static const int rank = _Rank;  
```  

## <a name="a-nametiledindextilea--tile"></a><a name="tiled_index__tile"></a>磁贴   
存储[索引](index-class.md)对象的秩为 1、 2 或 3 表示当前 tile 的坐标[tiled_extent](tiled-extent-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
const index<rank> tile;  
```  
  
## <a name="a-nametiledindextiledim0a--tiledim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0  
将存储的最重要的维度的长度。  
  
## <a name="syntax"></a>语法  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="a-nametiledindextiledim1a--tiledim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1   
将存储的下一步最不重要的维度的长度。  
  
## <a name="syntax"></a>语法  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="a-nametiledindextiledim2a--tiledim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2   
存储最不重要的维度的长度。  
  
## <a name="syntax"></a>语法  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="a-nametiledindextileorigina--tileorigin"></a><a name="tiled_index__tile_origin"></a>tile_origin   
存储[索引](index-class.md)对象中在当前 tile 的原点的级别 1、 2 或 3，表示全局坐标[tiled_extent](tiled-extent-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
const index<rank> tile_origin  
```  
## <a name="a-nametileextenta--tileextent"></a><a name="tile_extent"></a>tile_extent
  获取[扩展盘区](extent-class.md)对象，它具有的值`tiled_index`模板参数`tiled_index`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

