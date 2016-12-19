---
title: "编译器错误 C3382 | Microsoft Docs"
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
  - "C3382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3382"
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支持将“sizeof”与 \/clr:safe 一同使用  
  
 **\/clr:safe** 编译的输出文件是可验证类型安全的文件，不支持 sizeof ，因为 sizeof 运算符的返回值是 size\_t，其大小因操作系统而异。  
  
 有关详细信息，请参阅  
  
-   [sizeof 运算符](../../cpp/sizeof-operator.md)  
  
-   [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C\+\+ 64 位迁移的常见问题](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## 示例  
 下面的示例生成 C3382。  
  
```  
// C3382.cpp // compile with: /clr:safe int main() { sizeof( char );   // C3382 }  
```