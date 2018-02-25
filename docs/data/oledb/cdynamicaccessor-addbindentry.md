---
title: "Cdynamicaccessor:: Addbindentry |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8f139376-7db3-4193-ba3b-63fe938ffa79
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7234b06a32f53a24c5ccb9978ccc3910fa900807
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessoraddbindentry"></a>CDynamicAccessor::AddBindEntry
将绑定条目添加到输出列。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `info`  
 [in]A **DBCOLUMNINFO**结构，它包含列信息。 请参阅中的"DBCOLUMNINFO 结构" [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
## <a name="remarks"></a>备注  
 使用此方法时重写默认访问器使用创建`CDynamicAccessor`(请参阅[How Do I 提取的数据？](../../data/oledb/fetching-data.md))。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)