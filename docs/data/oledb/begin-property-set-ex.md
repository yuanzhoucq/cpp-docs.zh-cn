---
title: BEGIN_PROPERTY_SET_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BEGIN_PROPERTY_SET_EX
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPERTY_SET_EX macro
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46f20308e037942ef3259d930fa89a3e08dca93d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="beginpropertysetex"></a>BEGIN_PROPERTY_SET_EX
在属性中设置属性的开头的标记集映射。  
  
## <a name="syntax"></a>语法  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid  
, flags )  
```  
  
#### <a name="parameters"></a>参数  
 `guid`  
 [in]属性的 GUID 中。  
  
 `flags`  
 [in]**UPROPSET_HIDDEN**对于不希望公开，任何属性集或**UPROPSET_PASSTHROUGH**提供程序公开的提供程序的作用域之外定义的属性。  
  
## <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)