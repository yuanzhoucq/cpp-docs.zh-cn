---
title: IRowsetUpdateImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afbf8b42b4d518412c1004d78c5c718e54078c1c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340776"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 类
OLE DB 模板实现[IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 一个类派生自`IRowsetUpdateImpl`。  
  
 *存储*  
 用户记录中。  
  
 *UpdateArray*  
 一个数组，包含缓存数据以更新行集。  
  
 *RowClass*  
 为存储单元`HROW`。  
  
 *MapClass*  
 持有的提供程序的所有行句柄存储单元。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods-used-with-irowsetchange"></a>接口方法 （用于 IRowsetChange）  
  
|||  
|-|-|  
|[SetData](#setdata)|设置一个或多个列中的数据值。|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>接口方法 （用于 IRowsetUpdate）  
  
|||  
|-|-|  
|[GetOriginalData](#getoriginaldata)|获取最新传输到或从数据源，忽略挂起的更改中获取的数据。|  
|[GetPendingRows](#getpendingrows)|返回挂起的更改的行的列表。|  
|[GetRowStatus](#getrowstatus)|返回指定的行的状态。|  
|[撤消](#undo)|自上次提取或更新后撤消对行的任何更改。|  
|[更新](#update)|将传输自上次提取或更新以来对行进行任何更改。|  
  
### <a name="implementation-methods-callback"></a>实现方法 （回调）  
  
|||  
|-|-|  
|[IsUpdateAllowed](#isupdateallowed)|用于检查安全，完整性，等才允许更新。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_mapCachedData](#mapcacheddata)|包含延迟的操作的原始数据。|  
  
## <a name="remarks"></a>备注  
 您应首先阅读和理解的文档[IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)，这是因为存在所述的所有内容也在此处适用。 你还应阅读的第 6 章*OLE DB 程序员参考*上设置数据。  
  
 `IRowsetUpdateImpl` 实现 OLE DB`IRowsetUpdate`接口，可让使用者要延迟所做的更改传输`IRowsetChange`到数据源，并撤消在传输之前的更改。  
  
> [!IMPORTANT]
>  强烈建议您阅读以下文档，再尝试实现您的提供程序：  
  
-   [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)  
  
-   第 6 章*OLE DB 程序员参考*  
  
-   另请参阅如何`RUpdateRowset`UpdatePV 示例中使用类  

## <a name="setdata"></a> Irowsetupdateimpl:: Setdata
设置一个或多个列中的数据值。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[irowsetchange:: Setdata](https://msdn.microsoft.com/library/ms721232.aspx)中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  
 此方法重写[irowsetchangeimpl:: Setdata](../../data/oledb/irowsetchangeimpl-setdata.md)方法，但包括原始数据，以允许立即或延迟处理操作的缓存。

## <a name="getoriginaldata"></a> Irowsetupdateimpl:: Getoriginaldata
获取最新传输到或从数据源，忽略挂起的更改中获取的数据。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/library/ms709947.aspx)中*OLE DB 程序员参考*。   

## <a name="getpendingrows"></a> Irowsetupdateimpl:: Getpendingrows
返回挂起的更改的行的列表。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>参数  
 *hReserved*  
 [in]对应于*hChapter*中的参数[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx)。  
  
 其他参数，请参阅[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx)中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx)中*OLE DB 程序员参考*。  

## <a name="getrowstatus"></a> Irowsetupdateimpl:: Getrowstatus
返回指定的行的状态。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]);  
```  
  
#### <a name="parameters"></a>参数  
 *hReserved*  
 [in]对应于*hChapter*中的参数[IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/library/ms724377.aspx)。  
  
 其他参数，请参阅[IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/library/ms724377.aspx)中*OLE DB 程序员参考*。  

## <a name="undo"></a> Irowsetupdateimpl:: Undo
自上次提取或更新后撤消对行的任何更改。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>参数  
 *hReserved*  
 [in]对应于*hChapter*中的参数[IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)。  
  
 *pcRowsUndone*  
 [out]对应于*pcRows*中的参数[IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)。  
  
 *prgRowsUndone*  
 [in]对应于*prgRows*中的参数[IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)。  
  
 其他参数，请参阅[IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)中*OLE DB 程序员参考*。 

## <a name="update"></a> Irowsetupdateimpl:: Update
将传输自上次提取或更新以来对行进行任何更改。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>参数  
 *hReserved*  
 [in]对应于*hChapter*中的参数[irowsetupdate:: Update](https://msdn.microsoft.com/library/ms719709.aspx)。  
  
 其他参数，请参阅[irowsetupdate:: Update](https://msdn.microsoft.com/library/ms719709.aspx)中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  
 更改传输通过调用[irowsetchangeimpl:: Flushdata](../../data/oledb/irowsetchangeimpl-flushdata.md)。 使用者必须调用[CRowset::Update](../../data/oledb/crowset-update.md)的更改才会生效。 设置*prgRowstatus*为适当的值中所述[行状态](https://msdn.microsoft.com/library/ms722752.aspx)中*OLE DB 程序员参考*。 
  
## <a name="isupdateallowed"></a> Irowsetupdateimpl:: Isupdateallowed
重写此方法来检查安全性，完整性，更新之前，依此类推。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>参数  
 *status*  
 [in]挂起的操作的行的状态。  
  
 *hRowUpdate*  
 [in]用户想要更新的行的句柄。  
  
 *pRowStatus*  
 [out]向用户返回的状态。  
  
### <a name="remarks"></a>备注  
 如果你确定应允许更新，则返回 S_OK;否则，返回 E_FAIL。 如果允许更新，还需要设置`DBROWSTATUS`中[irowsetupdateimpl:: Update](../../data/oledb/irowsetupdateimpl-update.md)对相应[行状态](https://msdn.microsoft.com/library/ms722752.aspx)。  

## <a name="mapcacheddata"></a> Irowsetupdateimpl:: M_mapcacheddata
包含延迟的操作的原始数据的映射。  
  
### <a name="syntax"></a>语法  
  
```cpp
CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>参数  
 *hRow*  
 数据行的句柄。  
  
 *pData*  
 指向要缓存的数据的指针。 数据类型为*存储*（用户记录类）。 请参阅*存储*中的模板参数[IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)。  

## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)