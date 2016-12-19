---
title: "编译器错误 C3383 | Microsoft Docs"
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
  - "C3383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3383"
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支持将“operator new”与 \/clr:safe 一起使用  
  
 **\/clr:safe** 编译的输出文件可确保是类型安全的，且不支持指针。  
  
 有关详细信息，请参阅  
  
-   [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C\+\+ 64 位迁移的常见问题](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## 示例  
 下面的示例生成 C3383。  
  
```  
// C3383.cpp // compile with: /clr:safe int main() { char* pCharArray = new char[256];  // C3383 }  
```