---
title: "编译器错误 C3451 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3451"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3451"
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C3451
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“attribute”: 不能将非托管特性应用于“type”  
  
 不能将 C\+\+ 特性应用于 CLR 类型。  有关更多信息，请参见[C\+\+ Attributes Reference](../../windows/cpp-attributes-reference.md)。  
  
 有关详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 为 Visual C\+\+ 2005 执行的编译器一致性工作可能导致此错误：使用 CLR 编程的用户定义特性上不再允许有 [uuid](../../windows/uuid-cpp-attributes.md)特性。  请改用 <xref:System.Runtime.InteropServices.GuidAttribute>。  
  
## 示例  
 下面的示例生成 C3451。  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```