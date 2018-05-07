---
title: END_ACCESSOR |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- END_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR macro
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7bab52df0ed05886933a3df827fae5198651b39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="endaccessor"></a>END_ACCESSOR
将标记的末尾的访问器条目。  
  
## <a name="syntax"></a>语法  
  
```cpp
END_ACCESSOR()  
  
```  
  
## <a name="remarks"></a>备注  
 对于行集上的多个访问器，你需要指定`BEGIN_ACCESSOR_MAP`并用`BEGIN_ACCESSOR`的宏，每个单独的取值函数。 `BEGIN_ACCESSOR` 宏以 `END_ACCESSOR` 宏结束。 `BEGIN_ACCESSOR_MAP`宏已完成并且`END_ACCESSOR_MAP`宏。  
  
## <a name="example"></a>示例  
 请参阅[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)