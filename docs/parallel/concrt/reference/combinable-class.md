---
title: "combinable 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::combinable
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 4ed3ce3d441566a0fb301d01123335846d86a8af
ms.lasthandoff: 02/24/2017

---
# <a name="combinable-class"></a>combinable 类
`combinable<T>` 对象旨在提供数据的线程专用副本，以在并行算法期间执行无锁线程本地子计算。 在并行操作结束时，线程专用子计算可随之合并到最终结果。 此类可替代共享变量使用，并可能会带来性能提升（如果该共享变量上存在大量争用）。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>
class combinable;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 最终的合并结果数据类型。 该类型必须具有一个复制构造函数和默认构造函数。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[combinable 构造函数](#ctor)|已重载。 构造一个新`combinable`对象。|  
|[~ combinable 析构函数](#dtor)|销毁 `combinable` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[clear 方法](#clear)|清除所有中间的计算结果，从前面的用法。|  
|[combine 方法](#combine)|通过调用提供的 combine 伪函数计算的一套线程本地子计算的最终值。|  
|[combine_each 方法](#combine_each)|通过调用线程本地子计算每一次的提供的 combine 函子计算从线程本地子计算集的最终值。 最终结果被累积的函数对象。|  
|[本地方法](#local)|已重载。 返回对线程私有子计算的引用。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[运算符 = 运算符](#operator_eq)|将分配给`combinable`从另一个对象`combinable`对象。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `combinable`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namecleara-clear"></a><a name="clear"></a>清除 

 清除所有中间的计算结果，从前面的用法。  
  
```
void clear();
```  
  
##  <a name="a-namectora-combinable"></a><a name="ctor"></a>可组合 

 构造一个新`combinable`对象。  
  
```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 初始化伪函数对象的类型。  
  
 `_FnInitialize`  
 一个函数，它将调用以初始化类型的每个新线程私有值`T`。 它必须支持具有签名的函数调用运算符`T ()`。  
  
 `_Copy`  
 现有`combinable`要复制到此对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数初始化新元素的类型的默认构造函数`T`。  
  
 第二个构造函数初始化新元素使用与提供的初始化仿`_FnInitialize`参数。  
  
 第三个构造函数是复制构造函数。  
  
##  <a name="a-namedtora-combinable"></a><a name="dtor"></a>~ combinable 

 销毁 `combinable` 对象。  
  
```
~combinable();
```  
  
##  <a name="a-namecombinea-combine"></a><a name="combine"></a>组合 

 通过调用提供的 combine 伪函数计算的一套线程本地子计算的最终值。  
  
```
template<typename _Function>
T combine(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 将调用以组合两个线程本地子计算的函数对象类型。  
  
 `_FnCombine`  
 用于合并子计算函子。 其签名是`T (T, T)`或`T (const T&, const T&)`，并且它必须是结合并可交换。  
  
### <a name="return-value"></a>返回值  
 最终组合的结果，所有线程私有子计算。  
  
##  <a name="a-namecombineeacha-combineeach"></a><a name="combine_each"></a>combine_each 

 通过调用线程本地子计算每一次的提供的 combine 函子计算从线程本地子计算集的最终值。 最终结果被累积的函数对象。  
  
```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 将调用来合并单个的线程本地子计算的函数对象类型。  
  
 `_FnCombine`  
 用于组合某一子计算函子。 其签名是`void (T)`或`void (const T&)`，并且必须是结合并可交换。  
  
##  <a name="a-namelocala-local"></a><a name="local"></a>本地 

 返回对线程私有子计算的引用。  
  
```
T& local();

T& local(bool& _Exists);
```  
  
### <a name="parameters"></a>参数  
 `_Exists`  
 对一个布尔值的引用。 此参数引用的布尔值将设置为`true`子计算如果已存在该线程上并设置为`false`如果这是该线程上的第一个子计算。  
  
### <a name="return-value"></a>返回值  
 对线程私有子计算的引用。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 将分配给`combinable`从另一个对象`combinable`对象。  
  
```
combinable& operator= (const combinable& _Copy);
```  
  
### <a name="parameters"></a>参数  
 `_Copy`  
 现有`combinable`要复制到此对象。  
  
### <a name="return-value"></a>返回值  
 参考这`combinable`对象。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

