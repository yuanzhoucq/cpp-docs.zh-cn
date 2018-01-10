---
title: "BEGIN_ACCESSOR |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_ACCESSOR
dev_langs: C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f9461c508fe13a2930a39a2632d5a5a80f01c385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
标记访问器条目的开始。  
  
## <a name="syntax"></a>语法  
  
```  
  
BEGIN_ACCESSOR(  
num  
,   
bAuto  
 )  
  
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