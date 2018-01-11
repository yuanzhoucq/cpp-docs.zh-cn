---
title: "Cdbpropset:: Setguid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs: C++
helpviewer_keywords:
- SetGUID method
- AddProperty method
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0fed876cabd9a197d022a35829174bcc7e43e97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropsetsetguid"></a>CDBPropSet::SetGUID
集**guidPropertySet**字段**DBPROPSET**结构。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `guid`  
 [in]用于设置 GUID **guidPropertySet**字段[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构。  
  
## <a name="remarks"></a>备注  
 可以通过设置此字段[构造函数](../../data/oledb/cdbpropset-cdbpropset.md)以及。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDBPropSet 类](../../data/oledb/cdbpropset-class.md)