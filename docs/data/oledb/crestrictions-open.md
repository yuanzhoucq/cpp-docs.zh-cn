---
title: "Crestrictions:: Open |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c36d30c99cbf3e2e0b3366022bc2cec8591bbdf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crestrictionsopen"></a>CRestrictions::Open
返回一个结果集，根据用户提供的限制。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>参数  
 `session`  
 [in]指定用于连接到数据源的现有会话对象。  
  
 *lpszParam*  
 [in]架构行集上指定的限制。  
  
 `bBind`  
 [in]指定是否自动绑定列映射。 默认值是**true**，这将导致产生要自动绑定的列映射。 设置`bBind`到**false**阻止自动绑定列映射，以便你可以手动绑定。 （手动绑定是 OLAP 用户的特别感兴趣。）  
  
## <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
## <a name="remarks"></a>备注  
 架构行集上，可以指定最多七个限制。  
  
 请参阅[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)有关每个架构行集上定义的限制信息。  
  
## <a name="requirements"></a>要求  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)