---
title: "CAutoPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs: C++
helpviewer_keywords: CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b8ded7bbf4dbe4e4f2ada7054cebab996934316
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cautoptr-class"></a>CAutoPtr 类
此类表示一个智能指针对象。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 指针类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|构造函数。|  
|[CAutoPtr:: ~ CAutoPtr](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|调用此方法需要现有指针的所有权。|  
|[CAutoPtr::Detach](#detach)|调用此方法可释放的指针的所有权。|  
|[CAutoPtr::Free](#free)|调用此方法以删除指向的对象`CAutoPtr`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|强制转换运算符。|  
|[CAutoPtr::operator =](#operator_eq)|赋值运算符中。|  
|[CAutoPtr::operator->](#operator_ptr)|指针到成员运算符中。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|指针数据成员变量。|  
  
## <a name="remarks"></a>备注  
 此类提供用于创建和管理智能指针，这将有助于防止内存泄漏，通过它不再处于作用域时自动释放资源的方法。  
  
 此外，`CAutoPtr`的复制构造函数和赋值运算符传输所有权的指针，将源指针复制到目标指针并将源指针设置为 NULL。 因此不可能有两个`CAutoPtr`对象每个存储相同的指针，这减少了两次删除相同的指针的可能性。  
  
 `CAutoPtr`此外简化了创建的指针的集合。 而不是派生集合类和重写析构函数，它会更易于生成的集合`CAutoPtr`对象。 当删除集合时，`CAutoPtr`对象将超出范围并自动删除自己。  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)和变体的工作方式与`CAutoPtr`，只不过它们分配和释放内存而不 c + + 中使用不同的堆函数**新**和**删除**运算符。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)类似于`CAutoPtr`、 唯一的区别是它使用**矢量 new []**和**向量 delete []**分配和释放内存。  
  
 另请参阅[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)数组或列表的智能指针时需要。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>CAutoPtr::Attach  
 调用此方法需要现有指针的所有权。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 `CAutoPtr`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 当`CAutoPtr`对象采用的指针的所有权，它将自动删除指针和任何已分配的数据超出范围时。 如果[CAutoPtr::Detach](#detach)是调用，程序员再次给定负责释放任何分配资源。  
  
 调试版本中，如果断言失败会发生[CAutoPtr::m_p](#m_p)数据成员当前指向的现有值; 即，不等于 NULL。  
  
### <a name="example"></a>示例  
 请参阅中的示例[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="cautoptr"></a>CAutoPtr::CAutoPtr  
 构造函数。  
  
```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<> 
CAutoPtr(CAutoPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 现有的指针。  
  
 `TSrc`  
 由另一个类型`CAutoPtr`，用于初始化当前对象。  
  
### <a name="remarks"></a>备注  
 `CAutoPtr`可以使用现有指针创建对象，这种情况下它会将传输的指针的所有权。  
  
### <a name="example"></a>示例  
 请参阅中的示例[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="dtor"></a>CAutoPtr:: ~ CAutoPtr  
 析构函数。  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。 调用[CAutoPtr::Free](#free)。  
  
##  <a name="detach"></a>CAutoPtr::Detach  
 调用此方法可释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放的指针的所有权，设置[CAutoPtr::m_p](#m_p)数据成员变量为 NULL，并返回指针的副本。 在调用**分离**，它最多需要程序员来释放任何分配的资源对其`CAutoPtr`对象可能具有以前假设的 reponsibility。  
  
### <a name="example"></a>示例  
 请参阅中的示例[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="free"></a>CAutoPtr::Free  
 调用此方法以删除指向的对象`CAutoPtr`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>备注  
 指向的对象`CAutoPtr`将释放和[CAutoPtr::m_p](#m_p)数据成员变量设置为 NULL。  
  
##  <a name="m_p"></a>CAutoPtr::m_p  
 指针数据成员变量。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>备注  
 此成员变量包含的指针信息。  
  
##  <a name="operator_eq"></a>CAutoPtr::operator =  
 赋值运算符中。  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指针。  
  
 `TSrc`  
 类类型。  
  
### <a name="return-value"></a>返回值  
 返回的引用**CAutoPtr\< T >**。  
  
### <a name="remarks"></a>备注  
 赋值运算符分离`CAutoPtr`从任何当前指针的对象，并将附加新的指针， `p`，在其位置。  
  
### <a name="example"></a>示例  
 请参阅中的示例[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="operator_ptr"></a>CAutoPtr::operator-&gt;  
 指针到成员运算符中。  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CAutoPtr::m_p](#m_p)数据成员变量。  
  
### <a name="remarks"></a>备注  
 使用此运算符的指向类中调用的方法`CAutoPtr`对象。 调试版本中，如果断言失败会发生`CAutoPtr`点为 NULL。  
  
### <a name="example"></a>示例  
 请参阅中的示例[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="operator_t_star"></a>CAutoPtr::operator T *  
 强制转换运算符。  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>返回值  
 将指针返回到类模板中定义的对象数据类型。  
  
### <a name="example"></a>示例  
 请参阅中的示例[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [CHeapPtr 类](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr 类](../../atl/reference/cautovectorptr-class.md)   
 [类概述](../../atl/atl-class-overview.md)
