---
title: "编译器警告（等级 1）C4572 | Microsoft Docs"
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
  - "C4572"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4572"
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4572
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/clr 下的 \[ParamArray\] 特性已被弃用，请改用“...”  
  
 已使用用于指定变量参数列表的过时的样式。  编译 CLR 时，使用省略号语法而不是 <xref:System.ParamArrayAttribute>。  有关详细信息，请参阅[变量参数列表 \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C4572。  
  
```  
// C4572.cpp  
// compile with: /clr /W1  
void Func([System::ParamArray] array<int> ^);   // C4572  
void Func2(... array<int> ^){}   // OK  
  
int main() {  
   Func2(1, 2, 3);  
}  
```