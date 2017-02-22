---
title: "显式实例化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "模板，实例化"
  - "显式实例化"
  - "实例化，显式"
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 显式实例化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以通过显式实例化来创建一个实例化的模板类或函数，而不需实际使用您的代码。  由于该项在创建使用模板进行分发的库 \(.lib\) 文件时十分有用，因此未实例化的模板定义不放置到对象 \(.obj\) 文件中。  
  
 这个代码实例化显示`MyStack` 变量和 6 项 `int`：  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 这个报表创建了一个不能保留存储任何对象的实例 `MyStack` 。  代码生成了所有成员。  
  
 仅构造函数成员的函数才在下一行显式实例化：  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 你可以通过使用特定类型的自变量实例化显示函数模版并再次申明他们，就如模板所示[函数模板实例化](../cpp/function-template-instantiation.md)。  
  
 可以使用 `extern` 关键字防止成员自动实例化。  例如：  
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 同样，您能标记特定的成员作在外部同时不能被实例化：  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 你可以使用 `extern` 关键字使编译器在多个对象模块中生成相同的实例代码。  如果调用该函数，您必须在至少一个链接模块中通过显示指定的模版参数以实例化模板函数，否则您会在程序生成时收到链接器错误。  
  
> [!NOTE]
>  专用化中的 `extern` 关键字仅适用于定义在类主体外部的成员函数。  在类声明内定义的函数被视为内联函数，并始终实例化。  
  
## 请参阅  
 [函数模板](../cpp/function-templates.md)