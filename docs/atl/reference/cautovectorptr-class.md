---
title: "CAutoVectorPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAutoVectorPtr
- ATL.CAutoVectorPtr
- ATL.CAutoVectorPtr<T>
- CAutoVectorPtr
- ATL::CAutoVectorPtr<T>
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: bb4bbd110552d1e3cf604add44de7e428d2703ee
ms.lasthandoff: 02/24/2017

---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 类
此类表示智能指针对象使用向量 new 和 delete 运算符。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 指针类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|构造函数。|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|调用此方法来分配对指向的对象数组所需的内存`CAutoVectorPtr`。|  
|[CAutoVectorPtr::Attach](#attach)|调用此方法以获取现有指针的所有权。|  
|[CAutoVectorPtr::Detach](#detach)|调用此方法可释放的指针的所有权。|  
|[CAutoVectorPtr::Free](#free)|调用此方法可删除所指向的对象`CAutoVectorPtr`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|强制转换运算符。|  
|[CAutoVectorPtr::operator =](#operator_eq)|赋值运算符中。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|指针数据成员变量。|  
  
## <a name="remarks"></a>备注  
 此类提供用于创建和管理智能指针，这将有助于保护用户免受内存泄漏，它不再处于作用域时，会自动释放资源的方法。 `CAutoVectorPtr`类似于`CAutoPtr`、 唯一的区别在于，`CAutoVectorPtr`使用[矢量 new []](../../standard-library/new-operators.md#operator_new_arr)和[向量 delete []](../../standard-library/new-operators.md#operator_delete_arr)分配和释放内存而不是 c + +**新**和**删除**运算符。 请参阅[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)如果的集合类`CAutoVectorPtr`所需。  

  
 请参阅[CAutoPtr](../../atl/reference/cautoptr-class.md)有关使用智能指针类的示例。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-nameallocatea--cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Allocate  
 调用此方法来分配对指向的对象数组所需的内存`CAutoVectorPtr`。  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>参数  
 `nElements`  
 数组中的元素数。  
  
### <a name="return-value"></a>返回值  
 如果内存成功则返回 true 分配，失败的 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果将发生断言失败[CAutoVectorPtr::m_p](#m_p)成员变量当前指向的现有值; 也就是说，不等于 NULL。  
  
##  <a name="a-nameattacha--cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Attach  
 调用此方法以获取现有指针的所有权。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 `CAutoVectorPtr`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 当`CAutoVectorPtr`对象将拥有的指针的所有权，它将自动删除指针和任何已分配的数据超出范围时。 如果[CAutoVectorPtr::Detach](#detach)是调用，程序员所再次负责释放任何给定分配资源。  
  
 在调试版本中，如果将发生断言失败[CAutoVectorPtr::m_p](#m_p)成员变量当前指向的现有值; 也就是说，不等于 NULL。  
  
##  <a name="a-namecautovectorptra--cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
 构造函数。  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 现有的指针。  
  
### <a name="remarks"></a>备注  
 `CAutoVectorPtr`对象创建使用现有的指针，也可以在这种情况下它会将传输的指针的所有权。  
  
##  <a name="a-namedtora--cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 析构函数。  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。 调用[CAutoVectorPtr::Free](#free)。  
  
##  <a name="a-namedetacha--cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach  
 调用此方法可释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放指针的所有权，设置[CAutoVectorPtr::m_p](#m_p)成员变量为 NULL，并返回指针的副本。 在调用**分离**，它由编程人员以释放任何资源分配对其`CAutoVectorPtr`对象可能具有以前承担的责任。  
  
##  <a name="a-namefreea--cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Free  
 调用此方法可删除所指向的对象`CAutoVectorPtr`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>备注  
 指向的对象`CAutoVectorPtr`释放控制块和[CAutoVectorPtr::m_p](#m_p)成员变量设置为 NULL。  
  
##  <a name="a-namempa--cautovectorptrmp"></a><a name="m_p"></a>CAutoVectorPtr::m_p  
 指针数据成员变量。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>备注  
 此成员变量包含指针信息。  
  
##  <a name="a-nameoperatoreqa--cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::operator =  
 赋值运算符中。  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 一个指针。  
  
### <a name="return-value"></a>返回值  
 返回对**CAutoVectorPtr\< T&1;>**。  
  
### <a name="remarks"></a>备注  
 赋值运算符分离`CAutoVectorPtr`从任何当前指针的对象，并将附加的新指针`p`，在其位置。  
  
##  <a name="a-nameoperatortstara--cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 强制转换运算符。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>备注  
 为类模板中定义的对象数据类型返回的指针。  
  
## <a name="see-also"></a>另请参阅  
 [CAutoPtr 类](../../atl/reference/cautoptr-class.md)   
 [类概述](../../atl/atl-class-overview.md)

