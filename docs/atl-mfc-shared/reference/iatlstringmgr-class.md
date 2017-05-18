---
title: "IAtlStringMgr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: 16
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4ff4aa01a6d30f377560962f98a5892bdcc37837
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
|[克隆](#clone)|调用此方法以返回指向适用于的另一个实例的新字符串管理器的指针`CSimpleStringT`。|  
|[免费](#free)|调用此方法释放字符串数据结构。|  
|[GetNilString](#getnilstring)|返回一个指向`CStringData`空字符串对象所使用的对象。|  
|[重新分配](#reallocate)|调用此方法重新分配给字符串数据结构。|  
  
## <a name="remarks"></a>备注  
 此接口可管理所使用的 MFC 独立字符串类; 内存如[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)， [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)，和[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。  
  
 您可以使用此类为您的自定义字符串的类中实现自定义内存管理器。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpstr.h  
  
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
>  不要向失败的分配通过引发异常发送信号。 相反，由返回信号失败的分配**NULL**。  
  
### <a name="remarks"></a>备注  
 调用[IAtlStringMgr::Free](#free)或[IAtlStringMgr::ReAllocate](#reallocate)来释放由此方法分配的内存。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="clone"></a>IAtlStringMgr::Clone  
 将指针返回到适用于的另一个实例的新字符串经理`CSimpleStringT`。  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一份`IAtlStringMgr`对象。  
  
### <a name="remarks"></a>备注  
 通常由框架调用时字符串管理器所需的一个新字符串。 在大多数情况下，**这**返回指针。  
  
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
 释放以前分配的指定的内存块[分配](#allocate)或[重新分配](../../atl/reference/iatlmemmgr-class.md#reallocate)。  
  
> [!NOTE]
>  有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="getnilstring"></a>IAtlStringMgr::GetNilString  
 返回指向空字符串的字符串数据结构的指针。  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CStringData`对象用于表示空字符串。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回一个空字符串表示形式。  
  
> [!NOTE]
>  当实现自定义字符串管理器，此函数必须永远不会失败。 您可以确保这一点通过嵌入的一个实例**CNilStringData**字符串管理器类，并返回一个指针，到该实例中。  
  
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
 指向该内存管理器以前分配的内存指针。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)



