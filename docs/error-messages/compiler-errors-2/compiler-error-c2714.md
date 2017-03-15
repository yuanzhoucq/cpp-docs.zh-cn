---
title: "编译器错误 C2714 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2714"
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许使用 \_\_alignof\(void\)  
  
 传递给运算符一个无效值。  
  
 有关更多信息，请参见[\_\_alignof 运算符](../../cpp/alignof-operator.md)。  
  
## 示例  
 下面的示例生成 C2714。  
  
```  
// C2714.cpp  
int main() {  
   return __alignof(void);   // C2714  
   return __alignof(char);   // OK  
}  
```