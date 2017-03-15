---
title: "编译器错误 C2825 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2825"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2825"
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2825
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

var : 当后面跟“::”时必须为类或命名空间  
  
 尝试形成限定名的尝试失败。  
  
 例如，请确保代码不包含函数名以 :: 开头的函数声明。  
  
## 示例  
 下面的示例生成 C2825：  
  
```  
// C2825.cpp  
typedef int i;  
int main() {  
   int* p = new int;  
   p->i::i();   // C2825  
   // try the following line instead  
   // p->i::~i();  
}  
```