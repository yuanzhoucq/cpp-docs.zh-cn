---
title: "编译器错误 C2274 | Microsoft Docs"
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
  - "C2274"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2274"
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2274
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 位于“.”运算符右边时非法  
  
 类型作为成员访问运算符 \(.\) 的右操作数出现。  
  
 尝试访问用户定义的类型转换可能导致此错误。  请在句点和 `type` 之间使用关键字 `operator`。  
  
 下面的示例生成 C2286：  
  
```  
// C2274.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
  
int main() {  
   MyClass ClassName;  
   int i = ClassName.int();   // C2274  
   int j = ClassName.operator int();   // OK  
}  
```