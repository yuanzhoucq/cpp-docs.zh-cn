---
title: "CSimpleRow 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: efd6773edd5eaae8a53041eaab06e597fe029635
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="csimplerow-class"></a>CSimpleRow 类
提供的默认实现中使用行句柄， [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)类。  
  
## <a name="syntax"></a>语法

```cpp
class CSimpleRow  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|将引用计数添加到现有行句柄。|  
|[Compare](../../data/oledb/csimplerow-compare.md)|比较两个行，以查看它们是否引用相同的行实例。|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|构造函数。|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|释放行。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_dwRef](../../data/oledb/csimplerow-m-dwref.md)|为存在的行句柄的引用计数。|  
|[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)|表示光标的行集的索引。|  
  
## <a name="remarks"></a>备注  
 在逻辑上是结果行的唯一标记的行句柄。 `IRowsetImpl` 创建一个新`CSimpleRow`为每个行中请求[irowsetimpl:: Getnextrows](../../data/oledb/irowsetimpl-getnextrows.md)。 `CSimpleRow` 此外可以在按原样的默认模板自变量替换为您自己的行句柄，实现`IRowsetImpl`。 从而替换此类的唯一要求是能够提供接受类型的单个参数的构造函数替换类**长**。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)