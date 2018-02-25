---
title: rename_namespace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37b2c01479cb489f7ed573f55a48f5807161bf63
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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