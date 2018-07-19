---
title: CBulkRowset 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7dddf645b8795b12f6da70081327366b62946303
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090713"
---
# <a name="cbulkrowset-class"></a>CBulkRowset 类
提取和操作要通过检索多个行句柄，通过调用一次处理中大容量的数据行。  
  
## <a name="syntax"></a>语法

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 一个访问器类。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|递增引用计数。|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|构造函数。|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|检索数据，执行新的大容量提取必要的第一行。|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|将移动到最后一个行。|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|检索下的一行数据。|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|移动到的上一行。|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|该书签从提取用书签标记的行或指定的偏移量处的行。|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|提取行的行集中的小数部分位置 （从开始）。|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|设置当前行 (**m_nCurrentRow**) 为零，并释放所有行。|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|设置一次调用可以检索的行句柄数。|  
  
## <a name="example"></a>示例  
 下面的示例演示使用`CBulkRowset`类。  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)