---
title: "编译器错误 C2061 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2061"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2061"
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C2061
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误: 标识符“identifier”  
  
 编译器发现了不应在此出现的标识符。  请确保在使用 `identifier` 之前对其进行声明。  
  
 初始值设定项可能括在了括号中。  为避免该问题，请将声明符括在括号中或使其成为 `typedef`。  
  
 在编译器将表达式作为类模板参数检测时也可能导致此错误；使用 [typename](../../cpp/typename.md) 告诉编译器它是一个类型。  
  
 下面的示例生成 C2061：  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 如果将实例名传递该 [typeid](../../windows/typeid-cpp-component-extensions.md) 则会发生 C2061：  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```