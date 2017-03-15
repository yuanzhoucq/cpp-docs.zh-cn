---
title: "编译器警告（等级 1）C4964 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4964"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4964"
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4964
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未指定任何优化选项；将不会收集配置文件信息  
  
 指定了 [\/GL](../../build/reference/gl-whole-program-optimization.md) 和 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)，但未请求优化，所以不会生成任何 .pgc 文件，因此无法进行按配置文件优化。  
  
 如果要在运行应用程序时生成 .pgc 文件，请指定一个 [\/O](../../build/reference/o-options-optimize-code.md) 编译器选项。  
  
 下面的示例生成 C4964：  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```