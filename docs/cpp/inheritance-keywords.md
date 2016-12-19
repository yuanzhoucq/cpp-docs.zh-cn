---
title: "继承关键字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__multiple_inheritance"
  - "__single_inheritance_cpp"
  - "__virtual_inheritance_cpp"
  - "__virtual_inheritance"
  - "__multiple_inheritance_cpp"
  - "__single_inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__multiple_inheritance 关键字 [C++]"
  - "__single_inheritance 关键字 [C++]"
  - "__virtual_inheritance 关键字 [C++]"
  - "声明派生类"
  - "派生类, 声明"
  - "继承, 声明派生类"
  - "继承, 关键字"
  - "关键字 [C++], 继承关键字"
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 继承关键字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
```  
  
class [__single_inheritance] class-name; class [__multiple_inheritance] class-name; class [__virtual_inheritance] class-name;  
```  
  
 其中：  
  
 *class\-name*  
 要声明的类的名称。  
  
 C\+\+ 允许您在类定义前声明指向类成员的指针。  例如：  
  
```  
class S;  
int S::*p;  
```  
  
 在上面的代码中，将 `p` 声明为指向类 S 的整数成员的指针。  但此代码中尚未定义 `class S`；而只是声明它。  当编译器遇到此类指针时，它必须生成此指针的泛化表示形式。  表示形式的大小依赖于指定的继承模型。  可通过四种方式指定编译器的继承模型：  
  
-   在 IDE 中的**“指向成员的指针表示形式”**下  
  
-   在命令行中使用 [\/vmg](../build/reference/vmb-vmg-representation-method.md) 开关  
  
-   使用 [pointers\_to\_members](../preprocessor/pointers-to-members.md) 杂注  
  
-   使用继承关键字 `__single_inheritance`、`__multiple_inheritance` 和 `__virtual_inheritance`。  此技术控制每个类的继承模型。  
  
    > [!NOTE]
    >  如果在定义类后始终声明指向类成员的指针，则无需使用上述任何选项。  
  
 在类定义之前声明一个指向类成员的指针会影响生成的可执行文件的大小和速度。            类使用的继承越复杂，表示指向此类成员的指针所需的字节数以及解释指针所需的代码数就越大。  单一继承的复杂性最低，虚拟继承的复杂性最高。  
  
 如果将上面的示例更改为：  
  
```  
class __single_inheritance S;  
int S::*p;  
```  
  
 无论命令行选项或杂注如何，指向 `class S` 的成员的指针都将使用可能的最小表示形式。  
  
> [!NOTE]
>  类的指向成员的指针表示形式的同一向前声明应出现在声明指向该类的成员的指针的每个翻译单元中，并且声明应在声明指向成员的指针之前出现。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)