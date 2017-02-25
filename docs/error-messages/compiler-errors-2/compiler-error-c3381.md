---
title: "编译器错误 C3381 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3381"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3381"
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3381
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“assembly”: 只有在用 \/clr 选项编译的代码中才有程序集访问说明符  
  
 在程序集之外可以看到本机类型，但只能在 **\/clr** 编译中指定本机类型的程序集访问。  
  
 有关辅助功能和 WCAG 2.0 的更多信息，请参见[类型可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 和 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 下面的示例生成 C3381。  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```