---
title: "IAtlStringMgr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
dev_langs: C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85b99b0b1f35ecbc35b4096ac8c2260d0a55680d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 类
此类表示的接口`CStringT`内存管理器。  
  
## <a name="syntax"></a>语法  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[分配](#allocate)|调用此方法来分配新的字符串数据结构。|  
|[克隆](#clone)|调用此方法可用于与另一个实例一起使用的新字符串管理器中返回一个指向`CSimpleStringT`。|  
|[可用](#free)|调用此方法释放字符串数据结构。|  
|[GetNilString](#getnilstring)|返回一个指向`CStringData`空字符串对象所使用的对象。|  
|[重新分配](#reallocate)|调用此方法以重新分配的字符串数据结构。|  
  
## <a name="remarks"></a>备注  
 此接口管理独立于 MFC 的字符串类; 使用的内存如[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)， [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)，和[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。  
  
 此类还可用于为您自定义字符串的类中实现自定义的内存管理器。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsimpstr.h  
  
##  <a name="allocate"></a>IAtlStringMgr::Allocate  
 分配新的字符串数据结构。  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>参数  
 `nAllocLength`  
 新的内存块中的字符数。  
  
 `nCharSize`  
 字符串管理器使用的字符类型的大小 （以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配的内存块。  
  
> [!NOTE]
>  不发失败的分配信号通过引发异常。 相反，应通过返回终止的失败的分配**NULL**。  
  
### <a name="remarks"></a>备注  
 调用[IAtlStringMgr::Free](#free)或[IAtlStringMgr::ReAllocate](#reallocate)来释放由此方法分配的内存。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="clone"></a>IAtlStringMgr::Clone  
 将指针返回到用于与另一个实例一起使用的新字符串管理器`CSimpleStringT`。  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一份`IAtlStringMgr`对象。  
  
### <a name="remarks"></a>备注  
 通常，由框架调用字符串管理器需要为一个新字符串。 在大多数情况下，**这**指针会返回。  
  
 但是，如果内存管理器不支持正由多个实例`CSimpleStringT`，应返回指向可共享字符串管理器的指针。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="free"></a>IAtlStringMgr::Free  
 释放字符串数据结构。  
  
```
void Free(CStringData* pData) throw();
```  
  
### <a name="parameters"></a>参数  
 `pData`  
 指向要释放的内存块的指针。  
  
### <a name="remarks"></a>备注  
 释放以前分配的指定的内存块[分配](#allocate)或[都可重新分配](../../atl/reference/iatlmemmgr-class.md#reallocate)。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="getnilstring"></a>IAtlStringMgr::GetNilString  
 返回指向空字符串的字符串数据结构的指针。  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`CStringData`对象用于表示空字符串。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回一个空字符串表示形式。  
  
> [!NOTE]
>  当实现自定义字符串管理器，此函数必须永远不会失败。 你可以确保这一点通过将嵌入的实例**CNilStringData**字符串管理器类，并返回一个指针，该实例中。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="reallocate"></a>IAtlStringMgr::Reallocate  
 重新分配的字符串数据结构。  
  
```
CStringData* Reallocate(  
 CStringData* pData,
 int nAllocLength,
 int nCharSize) throw();
```  
  
### <a name="parameters"></a>参数  
 `pData`  
 指向此内存管理器以前分配的内存指针。  
  
 `nAllocLength`  
 新的内存块中的字符数。  
  
 `nCharSize`  
 字符串管理器使用的字符类型的大小 （以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配内存块的起始位置。  
  
### <a name="remarks"></a>备注  
 调用此函数可调整大小由指定的现有内存块`pData`。  
  
 调用[IAtlStringMgr::Free](#free)来释放由此方法分配的内存。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)


