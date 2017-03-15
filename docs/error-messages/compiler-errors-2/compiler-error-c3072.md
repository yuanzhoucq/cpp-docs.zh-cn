---
title: "编译器错误 C3072 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3072"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3072"
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3072
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

运算符“operator”不能应用于 ref 类的实例中  
  
 请使用一元“`operator`”运算符将 ref 类的实例转换为句柄类型  
  
 CLR 类型要求使用 CLR 运算符，而不是本机（或标准）运算符。有关详细信息，请参阅[% \(跟踪引用\)](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3072。  
  
```  
// C3072.cpp  
// compile with: /clr  
ref class R {};  
  
int main() {  
   R r1;  
   R^ r2 = &r1;   // C3072  
   R^ r3 = %r1;   // OK  
}  
```