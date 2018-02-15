---
title: "Platform::Collections::BackInsertIterator 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
dev_langs:
- C++
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23c8b657a6cafb720cf0be07e2e67b5af0d7767d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator 类
表示一个迭代器，它插入而非重写元素到有序集合的后端。  
  
## <a name="syntax"></a>语法  
  
```  
template <typename T>  
class BackInsertIterator : 
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 当前集合中项目的类型。  
  
### <a name="remarks"></a>备注  
 BackInsertIterator 类实现 [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md)所要求的规则。  
  
### <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[BackInsertIterator::BackInsertIterator](#ctor)|初始化 BackInsertIterator 类的新实例。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[BackInsertIterator::operator* 运算符](#operator-dereference)|检索对当前 BackInsertIterator 的引用。|  
|[BackInsertIterator::operator++ 运算符](#operator-increment)|返回对当前 BackInsertIterator 的引用。 迭代器未经修改。|  
|[BackInsertIterator::operator= 运算符](#operator-assign)|将指定对象追加到当前有序集合的末尾。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `BackInsertIterator`  
  
### <a name="requirements"></a>惠?  
 **标头：** collection.h  
  
 **命名空间：** Platform::Collections  
  
---
## <a name="ctor"></a>  Backinsertiterator:: Backinsertiterator 构造函数
初始化 `BackInsertIterator` 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
#### <a name="parameters"></a>参数  
 `v`  
 IVector\<T > 对象。  
  
### <a name="remarks"></a>备注  
 `BackInsertIterator` 在参数 `v` 指定的对象的最后一个元素之后插入元素。  
 
## <a name="operator-assign"></a>  Backinsertiterator:: Operator = 运算符
将指定对象追加到当前有序集合的末尾。  
  
## <a name="syntax"></a>语法  
  
```    
BackInsertIterator& operator=( const T& t);  
```  
  
#### <a name="parameters"></a>参数  
 `t`  
 要追加到当前集合的对象。  
  
### <a name="return-value"></a>返回值  
 对当前 BackInsertIterator 的引用。  

## <a name="operator-dereference"></a>  Backinsertiterator:: Operator * 运算符
检索对当前 BackInsertIterator 的引用。  
  
## <a name="syntax"></a>语法  
  
```  
BackInsertIterator& operator*();  
```  
  
### <a name="return-value"></a>返回值  
 对当前 BackInsertIterator 的引用。  
  
### <a name="remarks"></a>备注  
 此运算符返回对当前 BackInsertIterator 的引用；而不是对当前集合中任何元素的引用。  
 
## <a name="operator-increment"></a>  BackInsertIterator::operator++ Operator
返回对当前 BackInsertIterator 的引用。 迭代器未经修改。  
  
## <a name="syntax"></a>语法  
  
``` 
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(int);  
```  
  
### <a name="return-value"></a>返回值  
 对当前 BackInsertIterator 的引用。  
  
### <a name="remarks"></a>备注  
 按照设计，第一个语法示例前递增当前 BackInsertIterator，第二个语法后递增当前 BackInsertIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。  
  
 但是，此运算符不会实际修改 BackInsertIterator， 而是返回对未经修改的当前迭代器的引用。 这是相同的行为[运算符 *](#dereference-operator)。  
  
  
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)