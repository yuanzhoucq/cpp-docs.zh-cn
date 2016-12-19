---
title: "重命名 (#import) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Rename"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "重命名特性"
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 重命名 (#import)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 解决名称冲突问题。  
  
## 语法  
  
```  
rename("OldName","NewName")  
```  
  
#### 参数  
 `OldName`  
 类型库中的旧名称。  
  
 `NewName`  
 要替代旧名称使用的名称。  
  
## 备注  
 如果指定了此特性，编译器会将类型库中的 *OldName* 的所有匹配项替换为生成的标头文件中的用户提供的 *NewName*。  
  
 当类型库中的名称与系统标头文件中的宏定义一致时，可以使用此特性。  如果不解决这种情况，则会产生各种语法错误，如[编译器错误 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) 和[编译器错误 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。  
  
> [!NOTE]
>  该替换是针对类型库中使用的名称，而不是针对生成的标头文件中的名称。  
  
 例如，假设类型库中存在名为 `MyParent` 的属性，并且在标头文件中定义了宏 `GetMyParent`，在 `#import` 前面使用了该宏。  由于 `GetMyParent` 是错误处理 **get** 属性的包装器函数的默认名称，因此会发生名称冲突。  若要解决此问题，请在 `#import` 语句中使用以下特性：  
  
```  
rename("MyParent","MyParentX")  
```  
  
 该语句对类型库中的名称 `MyParent` 重命名。  尝试对 `GetMyParent` 包装器名称重命名将失败：  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 这是因为名称 `GetMyParent` 仅在生成的类型库标头文件中出现。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)