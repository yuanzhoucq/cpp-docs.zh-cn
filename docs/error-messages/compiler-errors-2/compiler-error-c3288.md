---
title: "编译器错误 C3288 | Microsoft Docs"
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
  - "C3288"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3288"
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3288
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 非法取消对句柄类型的引用  
  
 编译器检测到非法取消了对句柄类型的引用。  可以取消对句柄类型的引用，然后再将其分配给引用。  有关详细信息，请参阅[% \(跟踪引用\)](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3288。  
  
```  
// C3288.cpp  
// compile with: /clr  
ref class R {};  
int main() {  
   *(System::Object^) nullptr;   // C3288  
  
// OK  
   (System::Object^) nullptr;   // OK  
   R^ r;  
   R% pr = *r;  
}  
```