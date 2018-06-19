---
title: END_ACCESSOR_MAP |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- END_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR_MAP macro
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 647e581a86564221ad409caf9addd03ae3d11fb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101560"
---
# <a name="endaccessormap"></a>END_ACCESSOR_MAP
标记访问器映射条目的末尾。  
  
## <a name="syntax"></a>语法  
  
```cpp
END_ACCESSOR_MAP()  
  
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