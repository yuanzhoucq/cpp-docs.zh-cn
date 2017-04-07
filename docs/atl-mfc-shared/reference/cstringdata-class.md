---
title: "CStringData 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b7dfebebbec7acc774fa2e63ab9fafed788f679a
ms.lasthandoff: 02/24/2017

---
# <a name="cstringdata-class"></a>CStringData 类
此类表示一个字符串对象的数据。  
  
## <a name="syntax"></a>语法  
  
```
struct CStringData
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRef](#addref)|字符串数据对象的引用计数递增。|  
|[data](#data)|检索一个字符串对象的字符数据。|  
|[IsLocked](#islocked)|确定是否锁定了关联的字符串对象的缓冲区。|  
|[IsShared](#isshared)|确定是否关联的字符串对象的缓冲区的当前共享。|  
|[锁](#lock)|锁定关联的字符串对象的缓冲区。|  
|[发布](#release)|释放指定的字符串对象。|  
|[解除锁定](#unlock)|解除关联的字符串对象的缓冲区的锁定。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|在已分配的数据的长度`XCHAR`s （不包括终止 null)|  
|[nDataLength](#ndatalength)|当前使用中的数据的长度`XCHAR`s （不包括终止 null)|  
|[nRefs](#nrefs)|对象的当前引用计数。|  
|[pStringMgr](#pstringmgr)|此字符串对象的字符串管理器指向的指针。|  
  
## <a name="remarks"></a>备注  
 此类只应由开发人员实现自定义字符串管理器。 自定义字符串管理器的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 此类封装各种类型的信息和数据与更高版本的字符串对象，如关联[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)， [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)，或[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)对象。 每个更高版本的字符串对象包含一个指向其关联的`CStringData`对象，并且允许多个字符串对象以指向相同的字符串数据对象。 这种关系由引用计数 ( `nRefs`) 的`CStringData`对象。  
  
> [!NOTE]
>  在某些情况下，字符串类型 (如**CFixedString**) 不会与多个更高版本的字符串对象共享的字符串数据对象。 有关这方面的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 此数据组成︰  
  
-   内存管理器 (类型的[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) 的字符串。  
  
-   当前长度 ( [nDataLength](#ndatalength)) 的字符串。  
  
-   已分配的长度 ( [nAllocLength](#nalloclength)) 的字符串。 出于性能原因，这可能不同于当前的字符串长度  
  
-   当前的引用计数 ( [nRefs](#nrefs)) 的`CStringData`对象。 此值用于确定多少个字符串对象共享相同`CStringData`对象。  
  
-   实际字符缓冲区 ([数据](#data)) 的字符串。  
  
    > [!NOTE]
    >  字符串对象的实际字符缓冲区由字符串管理器分配并追加到`CStringData`对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpstr.h  
  
##  <a name="addref"></a>CStringData::AddRef  
 字符串对象的引用计数递增。  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>备注  
 字符串对象的引用计数递增。  
  
> [!NOTE]
>  不要对负引用计数，字符串中调用此方法，因为负计数指示字符串缓冲区被锁定。  
  
##  <a name="data"></a>CStringData::data  
 返回指向字符串对象的字符缓冲区的指针。  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>返回值  
 指向的字符串对象的字符缓冲区的指针。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回关联的字符串对象的当前字符缓冲区。  
  
> [!NOTE]
>  此缓冲区都没有分配`CStringData`对象而是由字符串管理器在需要时。 分配时，缓冲区将追加到字符串数据对象。  
  
##  <a name="islocked"></a>CStringData::IsLocked  
 确定字符缓冲区是否处于锁定状态。  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果缓冲区已被锁定; 否则为**false**。  
  
### <a name="remarks"></a>备注  
 调用此函数可确定当前已锁定的字符缓冲区的字符串对象。  
  
##  <a name="isshared"></a>CStringData::IsShared  
 确定是否共享字符缓冲区。  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果缓冲区已共享; 否则为**false**。  
  
### <a name="remarks"></a>备注  
 调用此函数可确定是否要在多个字符串对象之间当前共享的字符缓冲区的字符串数据对象。  
  
##  <a name="lock"></a>CStringData::Lock  
 锁定关联的字符串对象的字符缓冲区。  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>备注  
 调用此函数可锁定的字符缓冲区的字符串数据对象。 由开发人员需要直接访问权限的字符缓冲区时使用的锁定和解锁。 锁定的一个很好的示例所示[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。  
  
> [!NOTE]
>  如果缓冲区不在更高版本的字符串对象之间共享，则仅可以锁定字符缓冲区。  
  
##  <a name="nalloclength"></a>CStringData::nAllocLength  
 已分配的字符缓冲区的长度。  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>备注  
 将存储中的已分配的数据缓冲区的长度`XCHAR`s （不包括终止 null)。  
  
##  <a name="ndatalength"></a>CStringData::nDataLength  
 字符串对象的当前长度。  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>备注  
 将存储在当前使用的数据的长度`XCHAR`s （不包括终止 null)。  
  
##  <a name="nrefs"></a>CStringData::nRefs  
 字符串数据对象的引用计数。  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>备注  
 将存储的字符串数据对象的引用计数。 此计数指示更高版本与字符串数据对象相关联的字符串对象的数目。 负值表示字符串数据对象当前已锁定。  
  
##  <a name="pstringmgr"></a>CStringData::pStringMgr  
 关联的字符串对象的内存管理器。  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>备注  
 存储关联的字符串对象的内存管理器。 有关内存管理器和字符串的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="release"></a>CStringData::Release  
 字符串数据对象的引用计数递减。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>备注  
 调用此函数可减少引用计数，释放`CStringData`结构，如果引用计数达到零。 这通常是完成时的字符串对象被删除，因此不再需要进行引用的字符串数据对象。  
  
 例如，下面的代码将调用`CStringData::Release`与关联的字符串数据对象`str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&104;](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>CStringData::Unlock  
 解除关联的字符串对象的字符缓冲区的锁定。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>备注  
 调用此函数可解锁的字符缓冲区的字符串数据对象。 后一个缓冲区已解锁，都可以共享，并可能进行引用计数。  
  
> [!NOTE]
>  每次调用`Lock`必须由相应地调用匹配`Unlock`。  
  
 开发人员必须确保不共享的字符串数据时使用的锁定和解锁。 锁定的一个很好的示例所示[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)



