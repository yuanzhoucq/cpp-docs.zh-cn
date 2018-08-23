---
title: CHeapPtrBase 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d847c83fce13ea39c3032e7db638a91b1cb7ad85
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880315"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase 类
此类窗体智能堆指针的多个类的基础。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 要存储在堆上的对象类型。  
  
 *分配器*  
 要使用的内存分配类。 默认情况下使用的 CRT 例程来分配和释放内存。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|调用此方法来分配内存。|  
|[CHeapPtrBase::Attach](#attach)|调用此方法以获取现有指针的所有权。|  
|[CHeapPtrBase::Detach](#detach)|调用此方法释放的指针的所有权。|  
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
 此类窗体智能堆指针的多个类的基础。 派生的类，例如， [CHeapPtr](../../atl/reference/cheapptr-class.md)并[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，添加自己的构造函数和运算符。 请参阅这些类的实现示例。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
##  <a name="allocatebytes"></a>  CHeapPtrBase::AllocateBytes  
 调用此方法来分配内存。  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 *nBytes*  
 要分配的内存字节数。  
  
### <a name="return-value"></a>返回值  
 返回 true，如果内存已成功分配，false 否则。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果出现断言失败[CHeapPtrBase::m_pData](#m_pdata)成员变量目前指向的现有值; 即，不等于 NULL。  
  
##  <a name="attach"></a>  CHeapPtrBase::Attach  
 调用此方法以获取现有指针的所有权。  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>参数  
 *pData*  
 `CHeapPtrBase`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 当`CHeapPtrBase`对象采用的指针的所有权，它将自动删除指针和任何已分配的数据超出范围时。  
  
 在调试版本中，如果出现断言失败[CHeapPtrBase::m_pData](#m_pdata)成员变量目前指向的现有值; 即，不等于 NULL。  
  
##  <a name="dtor"></a>  CHeapPtrBase:: ~ CHeapPtrBase  
 析构函数。  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="detach"></a>  CHeapPtrBase::Detach  
 调用此方法释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放的指针的所有权，设置[CHeapPtrBase::m_pData](#m_pdata)成员变量为 NULL，并返回指针的副本。  
  
##  <a name="free"></a>  CHeapPtrBase::Free  
 调用此方法以删除指向的对象`CHeapPtrBase`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>备注  
 指向的对象`CHeapPtrBase`释放，并[CHeapPtrBase::m_pData](#m_pdata)成员变量设置为 NULL。  
  
##  <a name="m_pdata"></a>  CHeapPtrBase::m_pData  
 指针数据成员变量。  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>备注  
 此成员变量保存指针信息。  
  
##  <a name="operator_amp"></a>  CHeapPtrBase::operator &amp;  
 & 运算符。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回通过指向的对象的地址`CHeapPtrBase`对象。  
  

##  <a name="operator_ptr"></a>  CHeapPtrBase::operator-&gt;  

 指针到成员运算符中。  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CHeapPtrBase::m_pData](#m_pdata)成员变量。  
  
### <a name="remarks"></a>备注  
 使用此运算符将指向的类中调用方法`CHeapPtrBase`对象。 在调试版本中，如果出现断言失败`CHeapPtrBase`点为 NULL。  
  
##  <a name="operator_t_star"></a>  CHeapPtrBase::operator T *  
 强制转换运算符。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>备注  
 返回[CHeapPtrBase::m_pData](#m_pdata)。  
  
##  <a name="reallocatebytes"></a>  CHeapPtrBase::ReallocateBytes  
 调用此方法以重新分配内存。  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 *nBytes*  
 新的分配，以字节为单位的内存量。  
  
### <a name="return-value"></a>返回值  
 返回 true，如果内存已成功分配，false 否则。  
  
## <a name="see-also"></a>请参阅  
 [CHeapPtr 类](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)   
 [类概述](../../atl/atl-class-overview.md)
