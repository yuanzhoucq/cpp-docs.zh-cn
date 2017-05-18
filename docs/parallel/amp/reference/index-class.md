---
title: "index 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs:
- C++
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 52c19da3cb8de10c3963ca3b795cac1babb3dc7a
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

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
 级别、 级别或维度数。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[索引构造函数](#ctor)|初始化 `index` 类的新实例。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator--](#operator--)|递减的每个元素`index`对象。|  
|[operator(mod) =](#operator_mod_eq)|计算中每个元素的模数 （余数）`index`对象时某个数除该元素。|  
|[operator*=](#operator_star_eq)|将相乘的每个元素`index`由很多对象。|  
|[operator/=](#operator_div_eq)|将划分的每个元素`index`由很多对象。|  
|[index:: operator\[\]](#operator_at)|返回位于指定索引处的元素。|  
|[operator++](#operator_add_add)|递增的每个元素`index`对象。|  
|[operator+=](#operator_add_eq)|将指定的数加到的每个元素`index`对象。|  
|[operator=](#operator_eq)|将指定的内容复制`index`到此对象。|  
|[operator-=](#operator_-_eq)|从的每个元素指定的数中减去`index`对象。|  

  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|将存储的排名`index`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `index`  
  
## <a name="remarks"></a>备注  
 `index`结构均表示一个坐标向量*N*指定中的唯一位置的整数*N*-维空间。 对向量中的值按照从最重要到最不重要的顺序排列。 您可以使用的组件的值[运算符 =](#operator_eq)。  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  


## <a name="index_ctor"></a>索引构造函数
初始化 index 类的新实例。

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
（_I)  
中的一维索引的索引位置。  
_I0  
最重要的维的长度。  
_I1  
下一步-到-最高有效的维的长度。  
_I2  
最不重要的维的长度。  
_Other  
一个新的索引对象所基于的索引对象。  

## <a name="operator--"></a>操作符 —
减少索引对象的每个元素。  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>返回值
对于前缀运算符，该 index 对象 (* 这)。 对于后缀运算符，新的索引对象。

## <a name="operator_mod_eq"></a>operator(mod) =   
该元素被指定的数除时将计算该 index 对象中每个元素的模数 （余数）。

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>参数
_Rhs 要通过除法查找模数的数字。
返回值的索引对象。

## <a name="operator_star_eq"></a>运算符 * =   
返回由指定数量的索引对象的每个元素的乘积。
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数
_Rhs 要相乘的数字。

## <a name="operator_div_eq"></a>/ = 运算符 
除以指定数量的索引对象的每个元素。

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>参数
_Rhs 要除以的数字。

## <a name="operator_at"></a>operator\[\]  
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
_Index 从 0 到减 1 的排名的整数。

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

## <a name="operator_add_add"></a>operator + +   
递增索引对象的每个元素。
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>返回值
对于前缀运算符，该 index 对象 (* 这)。 对于后缀运算符，新的索引对象。

## <a name="operator_add_eq"></a>operator + =   
将指定的数加到每个元素的索引对象。
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
将指定的索引对象的内容复制到它。
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>参数
_Other 要从复制的索引对象。

### <a name="return-value"></a>返回值
对此索引对象的引用。

## <a name="operator_-_eq"></a>运算符 =
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

## <a name="rank"></a>排名  
  获取该 index 对象的秩。
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

