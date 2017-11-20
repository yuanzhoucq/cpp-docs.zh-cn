---
title: "no_auto_exclude |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_auto_exclude
dev_langs: C++
helpviewer_keywords: no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2b30760ba2021b13f84a0a56bde5ac41232fb443
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="noautoexclude"></a>no_auto_exclude
**C + + 专用**  
  
 禁用自动排除。  
  
## <a name="syntax"></a>语法  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>备注  
 类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 `#import` 尝试通过自动排除此类项来避免多个定义错误。 完成此操作后，[编译器警告 （等级 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)要排除的每一项，将发出。 您可以使用此特性来禁用此自动排除。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>另请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)