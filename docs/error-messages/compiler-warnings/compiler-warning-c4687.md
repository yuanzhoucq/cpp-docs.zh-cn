---
title: "编译器警告 C4687 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4687"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4687"
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告 C4687
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 密封抽象类无法实现接口“interface”  
  
 密封的抽象类型通常仅用于容纳静态成员函数。  
  
 有关更多信息，请参见[abstract](../../windows/abstract-cpp-component-extensions.md)和[sealed](../../windows/sealed-cpp-component-extensions.md)。  
  
 默认情况下，C4687 作为错误发出。  您可以用 [警告](../../preprocessor/warning.md) 杂注取消 C4687。  如果您确定要在密封的抽象类型中实现接口，可以取消 C4687。  
  
## 示例  
 下面的示例生成 C4687。  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```