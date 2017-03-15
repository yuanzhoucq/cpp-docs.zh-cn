---
title: "编译器错误 C2530 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2530"
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 必须初始化引用  
  
 在声明某个引用时必须初始化该引用，除非已经用下面的方法声明它：  
  
-   使用关键字 [extern](../../cpp/using-extern-to-specify-linkage.md)。  
  
-   作为类、结构或联合的成员（并且在构造函数中进行了初始化）。  
  
-   作为函数声明或定义中的参数。  
  
-   作为函数的返回类型。  
  
 下面的示例生成 C2530：  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```