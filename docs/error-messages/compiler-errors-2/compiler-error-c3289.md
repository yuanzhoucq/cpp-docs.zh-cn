---
title: "编译器错误 C3289 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3289"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3289"
ms.assetid: 3c1c623b-7fcf-43ab-a89a-8722532a8d29
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3289
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property”：无法索引 trivial 属性  
  
 未正确声明属性。 必须为索引的属性定义访问器。 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3289。  
  
```  
// C3289.cpp // compile with: /clr public ref struct C { // user-defined simple indexer property int indexer1[int];   // C3289 // user-defined indexer property int indexer2[int] { int get(int i) { return 0; } void set(int i, int j) {} } }; int main() { C ^ MyC = gcnew C(); MyC->indexer2[0] = 1; }  
```