---
title: "说明符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "声明说明符"
  - "声明, 说明符"
  - "说明符, 在声明中"
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题介绍了[声明](../misc/declarations.md)的*decl\-specifiers*（声明说明符）组件。  
  
 以下占位符和语言关键字为声明说明符：  
  
 *storage\-class\-specifier*  
  
 *type\-specifier*  
  
 *function\-specifier*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef](http://msdn.microsoft.com/zh-cn/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [\_\_declspec](../cpp/declspec.md) `(` *extended\-decl\-modifier\-seq* `)`  
  
## 备注  
 声明的 *decl\-specifiers* 部分是可以用来表示类型名称的 *decl\-specifiers* 的最长序列，不包括指针或引用修饰符。  声明的其余部分是 *declarator*，它包括引入的名称。  
  
 下表列出了四个声明，然后分别列出了每个声明的 *decl\-specifers* 和 *declarator* 组件。  
  
|声明|*decl\-specifiers*|`declarator`|  
|--------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 由于 `signed`、`unsigned`、`long` 和 `short` 都表示 `int`，因此将后跟以下任一关键字的 `typedef` 名称作为 *declarator\-list* 的成员，而不是 *decl\-specifiers* 的成员。  
  
> [!NOTE]
>  由于可以重新声明名称，因此其解释受当前范围内的最新声明的约束。  重新声明可能影响编译器解释名称的方式，尤其是 `typedef` 名称。  
  
## 请参阅  
 [声明](../misc/declarations.md)