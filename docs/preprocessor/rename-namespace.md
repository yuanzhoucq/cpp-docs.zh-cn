---
title: rename_namespace |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51114787dde2f858a8409538083282ef292d599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="renamenamespace"></a>rename_namespace
**C + + 专用**  
  
 重命名包含类型库内容的命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
rename_namespace("NewName")  
```  
  
#### <a name="parameters"></a>参数  
 `NewName`  
 命名空间的新名称。  
  
## <a name="remarks"></a>备注  
 它采用单个参数， *NewName*，它指定命名空间的新名称。  
  
 若要删除命名空间，使用[no_namespace](../preprocessor/no-namespace.md)特性。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)