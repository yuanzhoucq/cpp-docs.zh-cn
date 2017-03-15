---
title: "编译器错误 C3154 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3154"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3154"
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3154
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

省略号前面应为“,”。参数数组函数中不支持非逗号分隔的省略号。  
  
 未正确地声明变量参数函数。  
  
 有关详细信息，请参阅[变量参数列表 \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3154。  
  
```  
// C3154.cpp  
// compile with: /clr  
ref struct R {  
   void Func(int ... array<int> ^);   // C3154  
   void Func2(int i, ... array<int> ^){}   // OK  
   void Func3(array<int> ^){}   // OK  
   void Func4(... array<int> ^){}   // OK  
};  
  
int main() {  
   R ^ r = gcnew R;  
   r->Func4(1,2,3);  
}  
```