---
title: index 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs:
- C++
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594ee94bbbfc19bc6fcceb9ae7f0760d9ec877dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695332"
---
# <a name="index-class"></a>index 类
定义*N*-维索引 pographics cpp amp.md。  
  
## <a name="syntax"></a>语法  
  
```  
template <int _Rank>  
class index;  
```  
  
#### <a name="parameters"></a>参数  
 `_Rank`  
 秩或维度数。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[索引构造函数](#ctor)|初始化 `index` 类的新实例。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator--](#operator--)|递减的每个元素`index`对象。|  
|[operator(mod)=](#operator_mod_eq)|计算中每个元素的模数 （余数）`index`对象时该元素除以一个数字。|  
|[operator*=](#operator_star_eq)|乘以的每个元素`index`大量对象。|  
|[operator/=](#operator_div_eq)|将划分的每个元素`index`大量对象。|  
|[index::operator\[\]](#operator_at)|返回位于指定索引处的元素。|  
|[operator++](#operator_add_add)|递增的每个元素`index`对象。|  
|[operator+=](#operator_add_eq)|将指定的数添加到的每个元素`index`对象。|  
|[operator=](#operator_eq)|将指定的内容复制`index`到此对象。|  
|[operator-=](#operator_-_eq)|减去指定的数目的每个元素`index`对象。|  

  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|将存储的秩`index`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `index`  
  
## <a name="remarks"></a>备注  
 `index`结构表示的坐标向量*N*指定中的唯一位置的整数*N*-维空间。 向量中的值是从最高有效订购到最不重要。 您可以使用组件的值[运算符 =](#operator_eq)。  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  


## <a name="index_ctor"></a> 索引构造函数
初始化索引类的新实例。

```  
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
``` 

### <a name="parameters"></a>参数

_Array  
包含排名值的一维数组。  
_I  
一维索引中的索引位置。  
_I0  
最重要的维的长度。  
_I1  
下一步-到-最高有效的维度的长度。  
_I2  
最低有效的维度的长度。  
_Other  
一个新的索引对象所基于的索引对象。  

## <a name="operator--"></a>  运算符-
递减索引对象的每个元素。  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>返回值
对于前缀运算符，该 index 对象 (* 这)。 对于后缀运算符，新的索引对象。

## <a name="operator_mod_eq"></a>  operator(mod) =   
该元素除以指定数目时，请计算该 index 对象中每个元素的模数 （余数）。

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>参数
_Rhs 要通过除法查找模数的数字。
返回值的索引对象。

## <a name="operator_star_eq"></a>  operator*=   
返回按指定数的索引对象中的每个元素的乘积。
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数
_Rhs 要相乘的数字。

## <a name="operator_div_eq"></a>  / = 运算符 
指定的数除以索引对象中的每个元素。

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>参数
_Rhs 要被除的数字。

## <a name="operator_at"></a>  operator\[\]  
返回位于指定位置的索引的组件。

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数
_Index 一个介于 0 到减 1 的秩。

### <a name="return-value"></a>返回值
位于指定索引处的元素。

### <a name="remarks"></a>备注
下面的示例显示索引的组件值。
```  
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator++   
递增索引对象的每个元素。
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>返回值
对于前缀运算符，该 index 对象 (* 这)。 对于后缀运算符，新的索引对象。

## <a name="operator_add_eq"></a>  operator+=   
将指定的数添加到索引对象的每个元素。
```  
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>参数
_Rhs 要添加的数字。

### <a name="return-value"></a>返回值
索引对象中。

## <a name="operator_eq"></a>operator=   
将指定的索引对象的内容复制到此。
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>参数
_Other 要从复制的索引对象。

### <a name="return-value"></a>返回值
对此索引对象的引用。

## <a name="operator_-_eq"></a>  operator =
中减去指定的数目的索引对象的每个元素。
```  
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```  
### <a name="parameters"></a>参数
_Rhs 要减去的数字。

### <a name="return-value"></a>返回值
索引对象中。   

## <a name="rank"></a>  级别  
  获取该 index 对象的秩。
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
