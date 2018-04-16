---
title: "IRowsetChangeImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65463392c96bfa3563929ba64b62bd7454f25ba9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 类
OLE DB 模板实现[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) OLE DB 规范中的接口。  
  
## <a name="syntax"></a>语法

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 从派生的类`IRowsetChangeImpl`。  
  
 `Storage`  
 用户记录中。  
  
 `BaseInterface`  
 基类对于接口，如`IRowsetChange`。  
  
 `RowClass`  
 行句柄存储单元。  
  
 `MapClass`  
 提供程序持有的所有行句柄存储单元。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods-used-with-irowsetchange"></a>（与 IRowsetChange 一起使用） 的接口方法  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|从行集中删除行。|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|将行插入到行集。|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|设置一个或多个列中的数据值。|  
  
### <a name="implementation-method-callback"></a>实现方法 （回调）  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|通过提供商联系以将数据提交到其存储的替代。|  
  
## <a name="remarks"></a>备注  
 此接口是负责对数据存储区进行即时写入操作。 "即时"意味着，当最终用户 （使用使用者的人员） 进行任何更改，这些更改将立即传输到数据存储 （且不能撤消）。  
  
 `IRowsetChangeImpl` 实现 OLE DB`IRowsetChange`接口，可更新的现有行，删除行，并将插入新行中的列的值。  
  
 OLE DB 模板实现支持所有基方法 (`SetData`， `InsertRow`，和`DeleteRows`)。  
  
> [!IMPORTANT]
>  强烈建议你阅读以下文档后，再尝试实现你的提供商：  
  
-   [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)  
  
-   第 6 章*OLE DB 程序员参考*  
  
-   另请参阅如何`RUpdateRowset`UpdatePV 示例中使用类  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)