---
title: "CAutoVectorPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b01bb9f74793e739ff0930bae070f00cb909dd61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 类
此类表示智能指针对象在使用矢量 new 和 delete 运算符。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
  
|名称|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|构造函数。|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|调用此方法来分配所需的指向的对象的数组的内存`CAutoVectorPtr`。|  
|[CAutoVectorPtr::Attach](#attach)|调用此方法需要现有指针的所有权。|  
|[CAutoVectorPtr::Detach](#detach)|调用此方法可释放的指针的所有权。|  
|[CAutoVectorPtr::Free](#free)|调用此方法以删除指向的对象`CAutoVectorPtr`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|强制转换运算符。|  
|[CAutoVectorPtr::operator =](#operator_eq)|赋值运算符中。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|指针数据成员变量。|  
  
## <a name="remarks"></a>备注  
 此类提供用于创建和管理智能指针，这将有助于防止内存泄漏，通过它不再处于作用域时自动释放资源的方法。 `CAutoVectorPtr`类似于`CAutoPtr`、 唯一的区别是，`CAutoVectorPtr`使用[向量新 &#91; &#93;](../../standard-library/new-operators.md#op_new_arr)和[矢量删除 &#91; &#93;](../../standard-library/new-operators.md#op_delete_arr)分配和释放内存而不是c + +**新**和**删除**运算符。 请参阅[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)如果的集合类`CAutoVectorPtr`所需。  

  
 请参阅[CAutoPtr](../../atl/reference/cautoptr-class.md)有关使用智能指针类的示例。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="allocate"></a>CAutoVectorPtr::Allocate  
 调用此方法来分配所需的指向的对象的数组的内存`CAutoVectorPtr`。  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>参数  
 `nElements`  
 数组中的元素数。  
  
### <a name="return-value"></a>返回值  
 如果内存已成功，则返回 true 分配，失败的 false。  
  
### <a name="remarks"></a>备注  
 调试版本中，如果断言失败会发生[CAutoVectorPtr::m_p](#m_p)成员变量当前指向的现有值; 即，不等于 NULL。  
  
##  <a name="attach"></a>CAutoVectorPtr::Attach  
 调用此方法需要现有指针的所有权。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 `CAutoVectorPtr`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 当`CAutoVectorPtr`对象采用的指针的所有权，它将自动删除指针和任何已分配的数据超出范围时。 如果[CAutoVectorPtr::Detach](#detach)是调用，程序员再次给定负责释放任何分配资源。  
  
 调试版本中，如果断言失败会发生[CAutoVectorPtr::m_p](#m_p)成员变量当前指向的现有值; 即，不等于 NULL。  
  
##  <a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
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
 `CAutoVectorPtr`可以使用现有指针创建对象，这种情况下它会将传输的指针的所有权。  
  
##  <a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 析构函数。  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。 调用[CAutoVectorPtr::Free](#free)。  
  
##  <a name="detach"></a>CAutoVectorPtr::Detach  
 调用此方法可释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放的指针的所有权，设置[CAutoVectorPtr::m_p](#m_p)成员变量为 NULL，并返回指针的副本。 在调用**分离**，它最多需要程序员来释放任何分配的资源对其`CAutoVectorPtr`对象可能具有以前假设的责任。  
  
##  <a name="free"></a>CAutoVectorPtr::Free  
 调用此方法以删除指向的对象`CAutoVectorPtr`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>备注  
 指向的对象`CAutoVectorPtr`将释放和[CAutoVectorPtr::m_p](#m_p)成员变量设置为 NULL。  
  
##  <a name="m_p"></a>CAutoVectorPtr::m_p  
 指针数据成员变量。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>备注  
 此成员变量包含的指针信息。  
  
##  <a name="operator_eq"></a>CAutoVectorPtr::operator =  
 赋值运算符中。  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指针。  
  
### <a name="return-value"></a>返回值  
 返回的引用**CAutoVectorPtr\< T >**。  
  
### <a name="remarks"></a>备注  
 赋值运算符分离`CAutoVectorPtr`从任何当前指针的对象，并将附加新的指针， `p`，在其位置。  
  
##  <a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 强制转换运算符。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>备注  
 将指针返回到类模板中定义的对象数据类型。  
  
## <a name="see-also"></a>请参阅  
 [CAutoPtr 类](../../atl/reference/cautoptr-class.md)   
 [类概述](../../atl/atl-class-overview.md)
