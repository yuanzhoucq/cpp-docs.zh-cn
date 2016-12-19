---
title: "编译器错误 C2959 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2959"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2959"
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2959
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

泛型类或函数不能是模板的成员  
  
 有关更多信息，请参见[Windows 运行时和托管模板](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)和[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C2959。  
  
```  
// C2959.cpp  
// compile with: /clr /c  
template <class T> ref struct S {  
   generic <class U> ref struct GR1;   // C2959  
};  
```