---
title: "CStreamRowset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e499d732beb2d73dbb6ec0bbe0b360eeb394b9d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cstreamrowset-class"></a>CStreamRowset 类
在中使用`CCommand`或`CTable`声明。  
  
## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 一个访问器类。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|构造函数。 实例化和初始化`CStreamRowset`对象。|  
|[关闭](../../data/oledb/cstreamrowset-close.md)|版本[ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx)类中的接口指针。|  
  
## <a name="remarks"></a>备注  
 使用`CStreamRowset`中你`CCommand`或`CTable`声明，例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
 或  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` 返回`ISequentialStream`指针，它存储在`m_spStream`。 然后，你使用**读取**方法来检索 XML 格式 （Unicode 字符串） 的数据。 例如:  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 执行 XML 格式，并将返回所有列和行集作为一个 XML 字符串的所有行。  
  
> [!NOTE]
>  此功能仅适用于 SQL Server 2000。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)