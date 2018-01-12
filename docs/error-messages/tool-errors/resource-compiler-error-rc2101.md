---
title: "资源编译器错误 RC2101 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2101
dev_langs: C++
helpviewer_keywords: RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d08e9ddb7b8cda127b1d05bfef52b52833534cb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2101"></a>资源编译器错误 RC2101
预处理 RC 文件中的无效指令  
  
 资源编译器文件包含**#pragma**指令。  
  
 使用**#ifndef**带有 RC_INVOKED 常量资源编译器定义时它可以处理的包含文件的预处理器指令。 位置**#pragma**指令的定义 RC_INVOKED 常量时不处理的代码块。 仅由 C/c + + 编译器而不是资源编译器处理块中的代码。 下面的示例代码演示此技术：  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma**预处理器指令没有任何意义。RC 文件。 **#Include**中经常使用预处理器指令。RC 文件以包括标头文件 （基于项目的自定义标头文件或与某一产品由 Microsoft 提供的标准标头文件）。 其中一些包含文件包含**#pragma**指令。 由于标头文件可以包含一个或多个其他标头文件，包含有问题的文件**#pragma**指令可能不会即时显现。  
  
 **#Ifndef** RC_INVOKED 技术可以控制包括基于项目的标头文件中的标头文件。