---
title: "pointers_to_members | Microsoft Docs"
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
  - "pointers_to_members_CPP"
  - "vc-pragma.pointers_to_members"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "类成员, 指针指向"
  - "成员, 指针指向"
  - "pointers_to_members 杂注"
  - "杂注, pointers_to_members"
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointers_to_members
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定是否可以在类成员关联的类定义之前声明指向类成员的指针，以及类成员是否用于控制指针大小和解释指针所需的代码。  
  
## 语法  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## 备注  
 作为使用 [\/vmx](../build/reference/vmb-vmg-representation-method.md) 编译器选项或[继承关键字](../cpp/inheritance-keywords.md)的替代方式，您可以将 **pointers\_to\_members** 杂注放置在您的源文件中。  
  
 *pointer\-declaration* 参数指定是在关联的函数定义之前还是之后声明指向成员的指针。  *pointer\-declaration* 参数是下列两个符号之一：  
  
|参数|注释|  
|--------|--------|  
|**full\_generality**|生成安全的（有时并非最佳）代码。  如果在关联的类定义之前声明指向成员的任何指针，请使用 **full\_generality**。  此参数始终使用 *most\-general\-representation* 参数所指定的指针表示形式。  等效于 \/vmg。|  
|**best\_case**|使用指向成员的所有指针的最佳大小写表示形式生成安全的最佳代码。  要求在声明指向类成员的指针之前定义此类。  默认为 **best\_case**。|  
  
 *most\-general\-representation* 参数指定编译器可以安全地用来引用指向翻译单元中的类成员的任何指针的最小指针表示形式。  参数可以是下列项之一：  
  
|参数|注释|  
|--------|--------|  
|**single\_inheritance**|最常规的表示形式为单一继承（指向成员函数的指针）。  如果类定义（已为其声明指向成员的指针）的继承模型为多重继承或虚拟继承，则会导致出现错误。|  
|**multiple\_inheritance**|最常规的表示形式为多重继承（指向成员函数的指针）。  如果类定义（已为其声明指向成员的指针）的继承模型为虚拟继承，则会导致出现错误。|  
|**virtual\_inheritance**|最常规的表示形式为虚拟继承（指向成员函数的指针）。  绝不会导致出现错误。  这是使用 **\#pragma pointers\_to\_members\(full\_generality\)** 时的默认参数。|  
  
> [!CAUTION]
>  建议您仅将 `pointers_to_members` 杂注放置在要影响的源代码文件中以及所有 `#include` 指令之后。  此做法可以减小杂注影响其他文件以及为同一变量、函数或类名意外指定多个定义的风险。  
  
## 示例  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## 结束 C\+\+ 专用  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)