---
title: CDBPropSet::CDBPropSet | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropSet class, constructor
ms.assetid: 02ae5d9e-c067-47ca-8111-a03e86b5626b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: db118c9c814d957c43f11414ee583a2ccc7a416b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdbpropsetcdbpropset"></a>CDBPropSet::CDBPropSet
构造函数。 初始化**rgProperties**， **cProperties**，和**guidPropertySet**字段[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构。  
  
## <a name="syntax"></a>语法  
  
```cpp
      CDBPropSet(const GUID& guid);  

CDBPropSet(const CDBPropSet& propset);  

CDBPropSet();  
```  
  
#### <a name="parameters"></a>参数  
 `guid`  
 [in]用于初始化 GUID **guidPropertySet**字段。  
  
 *propset*  
 [in] 复制构造的另一个 `CDBPropSet` 对象。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDBPropSet 类](../../data/oledb/cdbpropset-class.md)   
 [CDBPropSet::SetGUID](../../data/oledb/cdbpropset-setguid.md)   
 [需要的 DBPROP 结构](https://msdn.microsoft.com/en-us/library/ms717970.aspx)