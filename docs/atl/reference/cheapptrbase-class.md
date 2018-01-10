---
title: "CHeapPtrBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs: C++
helpviewer_keywords: CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59520211ae577c4ca4358874ef1d8ff71de59921
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase 类
此类窗体智能堆指针的多个类的基础。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在堆的对象类型。  
  
 `Allocator`  
 要使用的内存分配类。 默认情况下，CRT 例程用于分配和释放内存。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|调用此方法以分配内存。|  
|[CHeapPtrBase::Attach](#attach)|调用此方法需要现有指针的所有权。|  
|[CHeapPtrBase::Detach](#detach)|调用此方法可释放的指针的所有权。|  
|[CHeapPtrBase::Free](#free)|调用此方法以删除指向的对象`CHeapPtrBase`。|  
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|调用此方法以重新分配内存。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrBase::operator T *](#operator_t_star)|强制转换运算符。|  
|[CHeapPtrBase::operator （& a)](#operator_amp)|& 运算符。|  
|[CHeapPtrBase::operator->](#operator_ptr)|指针到成员运算符中。|  

  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrBase::m_pData](#m_pdata)|指针数据成员变量。|  
  
## <a name="remarks"></a>备注  
 此类窗体智能堆指针的多个类的基础。 派生的类，例如， [CHeapPtr](../../atl/reference/cheapptr-class.md)和[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，添加自己的构造函数和运算符。 请参阅这些类的实现示例。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcore.h  
  
##  <a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes  
 调用此方法以分配内存。  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 要分配的内存的字节数。  
  
### <a name="return-value"></a>返回值  
 如果内存已成功，则返回 true 分配，false 否则。  
  
### <a name="remarks"></a>备注  
 调试版本中，如果断言失败会发生[CHeapPtrBase::m_pData](#m_pdata)成员变量当前指向的现有值; 即，不等于 NULL。  
  
##  <a name="attach"></a>CHeapPtrBase::Attach  
 调用此方法需要现有指针的所有权。  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>参数  
 `pData`  
 `CHeapPtrBase`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 当`CHeapPtrBase`对象采用的指针的所有权，它将自动删除指针和任何已分配的数据超出范围时。  
  
 调试版本中，如果断言失败会发生[CHeapPtrBase::m_pData](#m_pdata)成员变量当前指向的现有值; 即，不等于 NULL。  
  
##  <a name="dtor"></a>CHeapPtrBase:: ~ CHeapPtrBase  
 析构函数。  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="detach"></a>CHeapPtrBase::Detach  
 调用此方法可释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放的指针的所有权，设置[CHeapPtrBase::m_pData](#m_pdata)成员变量为 NULL，并返回指针的副本。  
  
##  <a name="free"></a>CHeapPtrBase::Free  
 调用此方法以删除指向的对象`CHeapPtrBase`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>备注  
 指向的对象`CHeapPtrBase`将释放和[CHeapPtrBase::m_pData](#m_pdata)成员变量设置为 NULL。  
  
##  <a name="m_pdata"></a>CHeapPtrBase::m_pData  
 指针数据成员变量。  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>备注  
 此成员变量包含的指针信息。  
  
##  <a name="operator_amp"></a>CHeapPtrBase::operator&amp;  
 & 运算符。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指向对象的地址`CHeapPtrBase`对象。  
  

##  <a name="operator_ptr"></a>CHeapPtrBase::operator-&gt;  

 指针到成员运算符中。  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CHeapPtrBase::m_pData](#m_pdata)成员变量。  
  
### <a name="remarks"></a>备注  
 使用此运算符的指向类中调用的方法`CHeapPtrBase`对象。 调试版本中，如果断言失败会发生`CHeapPtrBase`点为 NULL。  
  
##  <a name="operator_t_star"></a>CHeapPtrBase::operator T *  
 强制转换运算符。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>备注  
 返回[CHeapPtrBase::m_pData](#m_pdata)。  
  
##  <a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes  
 调用此方法以重新分配内存。  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 新的分配，以字节为单位的内存量。  
  
### <a name="return-value"></a>返回值  
 如果内存已成功，则返回 true 分配，false 否则。  
  
## <a name="see-also"></a>请参阅  
 [CHeapPtr 类](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)   
 [类概述](../../atl/atl-class-overview.md)
