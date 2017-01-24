---
title: "编译器警告 C4430 | Microsoft Docs"
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
  - "C4430"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4430"
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4430
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

缺少类型说明符 \- 假定为 int。注意：C\+\+ 不支持默认 int  
  
 对 Visual C\+\+ 2005 执行的编译器一致性工作可能导致此错误：所有声明必须显式指定类型；不再假定为 int。  
  
 C4430 始终作为错误发出。可以使用 `#pragma warning` 或 **\/wd** 关闭此警告；有关更多信息，请参见 [警告](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won（警告等级）](../../build/reference/compiler-option-warning-level.md)。  
  
## 示例  
 下面的示例生成 C4430。  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```