---
title: "编译器错误 C2472 | Microsoft Docs"
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
  - "C2472"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2472"
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2472
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”无法在托管代码“message”中生成；请使用 \/clr 进行编译以生成混合映像  
  
 当在纯公共语言运行库 \(CLR\) 环境中使用托管代码不支持的类型时，将出现此错误。 请使用 **\/clr** 进行编译以解决该错误。  
  
## 示例  
 下面的示例生成 C2472。  
  
```  
// C2472.cpp // compile with: /clr:pure // C2472 expected #include <cstdlib> int main() { int * __ptr32 p32; int * __ptr64 p64; p32 = (int * __ptr32)malloc(4); p64 = p32; }  
```  
  
## 请参阅  
 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)