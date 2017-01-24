---
title: "编译器警告（等级 1）C4288 | Microsoft Docs"
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
  - "C4288"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4288"
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4288
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 :“var”: 在 For 循环中声明的循环控制变量用在了 For 循环范围外；它与外部范围内的声明冲突  
  
 当用 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 和 **\/Zc:forscope\-** 编译时，在 [for](../../cpp/for-statement-cpp.md) 循环范围之后使用了 **for** 循环中声明的变量。  C\+\+ 语言的 Microsoft 扩展允许该变量保留在范围中，并且 C4288 提醒您不使用第一个声明的变量。  
  
 有关如何用 \/Ze 指定 **for** 循环中的 Microsoft 扩展的信息，请参见 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)。  
  
 下面的示例生成 C4288：  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```