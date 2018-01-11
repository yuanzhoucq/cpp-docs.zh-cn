---
title: "IRowsetImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IRowsetImpl
dev_langs: C++
helpviewer_keywords: IRowsetImpl class
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b4d8dd6f6dced2b4847939b0d7ed560f1d59479
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimpl-class"></a>IRowsetImpl 类
提供 `IRowset` 接口的实现。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*   
   >  
>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IRowsetImpl`。  
  
 `RowsetInterface`  
 从派生的类`IRowsetImpl`。  
  
 `RowClass`  
 有关存储单元**HROW**。  
  
 `MapClass`  
 提供程序持有的所有行句柄的存储单位。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|将引用计数添加到现有行句柄。|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|由调用[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)分配一个新**HROW**。 不直接由用户调用。|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|从行的行集的副本检索数据。|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|返回指定字段的状态。|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|记住的以前的位置按顺序，提取行。|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|构造函数。 不直接由用户调用。|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|由调用[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)。 不直接由用户调用。|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|释放行。|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|将下次提取位置重新定位到其初始位置;即，创建第一个行集时其位置。|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|设置指定字段的状态标志。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|指示提供程序是否支持向后提取。|  
|[m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|指示提供程序是否可以向后具有其游标滚动。|  
|[m_bReset](../../data/oledb/irowsetimpl-m-breset.md)|指示提供程序是否已重置其光标位置。 这具有特殊含义时向后滚动或向后在提取[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)。|  
|[m_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|表示光标的行集的索引。|  
|[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|行句柄的列表。|  
  
## <a name="remarks"></a>备注  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)是基行集接口。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)