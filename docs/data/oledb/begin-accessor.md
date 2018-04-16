---
title: BEGIN_ACCESSOR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac11ee19a626a945500bd9acb95cbe8ce0823d82
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
标记访问器条目的开始。  
  
## <a name="syntax"></a>语法  
  
```  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>参数  
 *num*  
 [in]此地图中的访问器访问器零偏移量。  
  
 *bAuto*  
 [in]指定此访问器是否为自动访问器或手动访问器。 如果**true**，访问器自动; 如果**false**，访问器是否为手动。 为自动访问器意味着提取数据以供你在移动操作。  
  
## <a name="remarks"></a>备注  
 对于行集上的多个访问器，你必须指定`BEGIN_ACCESSOR_MAP`并用`BEGIN_ACCESSOR`的宏，每个单独的取值函数。 `BEGIN_ACCESSOR` 宏以 `END_ACCESSOR` 宏结束。 `BEGIN_ACCESSOR_MAP`宏已完成并且`END_ACCESSOR_MAP`宏。  
  
## <a name="example"></a>示例  
 请参阅[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)