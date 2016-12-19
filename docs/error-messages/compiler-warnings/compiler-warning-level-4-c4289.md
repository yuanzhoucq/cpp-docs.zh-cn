---
title: "编译器警告（等级 4）C4289 | Microsoft Docs"
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
  - "C4289"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4289"
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4289
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 :“var”: 在 for 循环中声明的循环控制变量用在了 for 循环范围外  
  
 当用 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 和 **\/Zc:forScope\-** 编译时，在 **for** 循环范围之后使用了 [for](../../cpp/for-statement-cpp.md) 循环中声明的变量。  
  
 有关如何用 **\/Ze** 指定 **for** 循环中的标准行为的信息，请参见 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4289：  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```