---
title: "tiled_extent 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::tiled_extent
dev_langs:
- C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
caps.latest.revision: 9
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
ms.openlocfilehash: c2f7ebdb9c82ae24cf74064e710ddfb177670359
ms.lasthandoff: 02/24/2017

---
# <a name="tiledextent-class"></a>tiled_extent 类
一个`tiled_extent`对象是`extent`一到三个维度的对象，该对象的扩展盘区空间细分到一个、 两个或三维磁贴。  
  
### <a name="syntax"></a>语法  
  
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
  
### <a name="parameters"></a>参数  
 `_Dim0`  
 最重要的维的长度。  
  
 `_Dim1`  
 下一步最不重要的维度的长度。  
  
 `_Dim2`  
 最不重要的维的长度。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[tiled_extent 构造函数](#ctor)|初始化 `tiled_extent` 类的新实例。|  

  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_tile_extent 方法](#tiled_extent__get_tile_extent)|返回`extent`捕获的值的对象`tiled_extent`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。|  
|[填充方法](#tiled_extent__pad)|返回一个新`tiled_extent`具有扩展盘区对象上可调整以使整除的磁贴尺寸。|  
|[truncate 方法](#tiled_extent__truncate)|返回一个新`tiled_extent`具有扩展盘区对象下可调整以使整除的磁贴尺寸。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[运算符 = 运算符](#operator_eq)|将指定的内容复制`tiled_index`到此对象。|  

  
### <a name="public-constants"></a>公共常量  
  
|名称|说明|  
|----------|-----------------|  
|[tile_dim0 常量](#tiled_extent__tile_dim0)|将存储的最重要的维度的长度。|  
|[tile_dim1 常量](#tiled_extent__tile_dim1)|将存储的下一步最不重要的维度的长度。|  
|[tile_dim2 常量](#tiled_extent__tile_dim2)|存储最不重要的维度的长度。|  

  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[tile_extent 数据成员](#tiled_extent__tile_extent)|获取`extent`捕获的值的对象`tiled_extent`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `extent`  
  
 `tiled_extent`  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  

## <a name="tiled_extent__ctor"></a> tiled_extent 构造函数  
初始化 `tiled_extent` 类的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
tiled_extent();  
  
tiled_extent(  
    const Concurrency::extent<rank>& _Other );  
  
tiled_extent(  
    const tiled_extent& _Other );  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `extent`或`tiled_extent`要从中复制对象。  
  

  

## <a name="tiled_extent__get_tile_extent"></a> get_tile_extent   
返回`extent`捕获的值的对象`tiled_extent`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。  
  
### <a name="syntax"></a>语法  
  
```  
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>返回值  
 `extent`捕获此维度的对象`tiled_extent`实例。  
  

## <a name="tiled_extent__pad"></a>  pad   
返回一个新`tiled_extent`具有扩展盘区对象上可调整以使整除的磁贴尺寸。  
  
### <a name="syntax"></a>语法  
  
```  
tiled_extent pad() const;  
```  
  
### <a name="return-value"></a>返回值  
 新`tiled_extent`对象按值。 
## <a name="tiled_extent__truncate"></a>截断   
返回一个新`tiled_extent`具有扩展盘区对象下可调整以使整除的磁贴尺寸。  
  
### <a name="syntax"></a>语法  
  
```  
tiled_extent truncate() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回一个新`tiled_extent`具有扩展盘区对象下可调整以使整除的磁贴尺寸。  

## <a name="tiled_extent__operator_eq"></a>运算符 =   
将指定的内容复制`tiled_index`到此对象。  
  
### <a name="syntax"></a>语法  
  
```  
tiled_extent&  operator= (  
    const tiled_extent& _Other ) restrict (amp, cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `tiled_index`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这`tiled_index`实例。  

## <a name="tiled_extent__tile_dim0"></a> tile_dim0   
将存储的最重要的维度的长度。  
  
### <a name="syntax"></a>语法  
  
```  
static const int tile_dim0 = _Dim0;  
```  
  
## <a name="tiled_extent__tile_dim1"></a> tile_dim1   
将存储的下一步最不重要的维度的长度。  
  
### <a name="syntax"></a>语法  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tiled_extent__tile_dim2"></a> tile_dim2   
存储最不重要的维度的长度。  
  
### <a name="syntax"></a>语法  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tiled_extent__tile_extent"></a> tile_extent   
  获取`extent`捕获的值的对象`tiled_extent`模板参数`_Dim0`， `_Dim1`，和`_Dim2`。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;  
```  
  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

