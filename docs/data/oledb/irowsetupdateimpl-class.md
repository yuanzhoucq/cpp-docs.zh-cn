---
title: IRowsetUpdateImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34efd252f67a0e3da9827ef97cff8bcab0a45532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110431"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 类
OLE DB 模板实现[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)接口。  
  
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
  
#### <a name="parameters"></a>参数  
 `T`  
 从派生的类`IRowsetUpdateImpl`。  
  
 `Storage`  
 用户记录中。  
  
 `UpdateArray`  
 包含用于更新行集的缓存的数据的数组。  
  
 `RowClass`  
 存储单位**HROW**。  
  
 `MapClass`  
 提供程序持有的所有行句柄存储单元。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods-used-with-irowsetchange"></a>（与 IRowsetChange 一起使用） 的接口方法  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|设置一个或多个列中的数据值。|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>（与 IRowsetUpdate 一起使用） 的接口方法  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|获取最近传输到或从忽略挂起的更改的数据源中获取的数据。|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|返回具有挂起的更改的行的列表。|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|返回指定的行的状态。|  
|[撤消](../../data/oledb/irowsetupdateimpl-undo.md)|自上次提取或更新以来撤消对行的任何更改。|  
|[更新](../../data/oledb/irowsetupdateimpl-update.md)|传输自上次提取或更新后对行进行任何更改。|  
  
### <a name="implementation-methods-callback"></a>实现方法 （回调）  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|用于为安全起见，完整性，依次类推之前允许更新检查。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|包含原始数据延迟的操作。|  
  
## <a name="remarks"></a>备注  
 你应首先阅读并理解的文档[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)，这是因为存在所述的所有内容也适用此处。 你还应阅读的第 6 章*OLE DB 程序员参考*上设置数据。  
  
 `IRowsetUpdateImpl` 实现 OLE DB`IRowsetUpdate`接口，可使用者延迟所做的更改传输`IRowsetChange`到数据源，并撤消在传输之前的更改。  
  
> [!IMPORTANT]
>  强烈建议你阅读以下文档后，再尝试实现你的提供商：  
  
-   [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)  
  
-   第 6 章*OLE DB 程序员参考*  
  
-   另请参阅如何`RUpdateRowset`UpdatePV 示例中使用类  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)