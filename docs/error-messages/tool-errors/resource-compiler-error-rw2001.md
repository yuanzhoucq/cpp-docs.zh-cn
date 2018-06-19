---
title: 资源编译器错误 RW2001 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 077260b615d0a5adf32278d8857df5b8f74b7e5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321095"
---
# <a name="resource-compiler-error-rw2001"></a>资源编译器错误 RW2001
预处理 RC 文件中的无效指令  
  
 RC 文件包含 **#pragma**指令。  
  
 使用 **#ifndef**使用预处理器指令**RC_INVOKED**常量资源编译器定义时它可以处理的包含文件。 位置 **#pragma**指令不代码块中处理时**RC_INVOKED**定义常量。 仅由 C/c + + 编译器而不是资源编译器处理块中的代码。 下面的示例代码演示此技术：  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma**预处理器指令没有任何意义。RC 文件。 **#Include**中经常使用预处理器指令。RC 文件以包括标头文件 （基于项目的自定义标头文件或与某一产品由 Microsoft 提供的标准标头文件）。 其中一些包含文件包含 **#pragma**指令。 由于标头文件可以包含一个或多个其他标头文件，包含有问题的文件 **#pragma**指令可能不会即时显现。  
  
 **#Ifndef RC_INVOKED**技术可以控制包括基于项目的标头文件中的标头文件。