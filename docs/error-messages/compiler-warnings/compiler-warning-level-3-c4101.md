---
title: "编译器警告（等级 3）C4101 | Microsoft Docs"
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
  - "C4101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4101"
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4101
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 未引用的局部变量  
  
 从未使用局部变量。  在以下明显情况下显示该警告：  
  
```  
// C4101a.cpp  
// compile with: /W3  
int main() {  
int i;   // C4101  
}  
```  
  
 但是，当通过类的实例调用 **static** 成员函数时，也将显示该警告：  
  
```  
// C4101b.cpp  
// compile with:  /W3  
struct S {  
   static int func()  
   {  
      return 1;  
   }  
};  
  
int main() {  
   S si;   // C4101, si is never used  
   int y = si.func();  
   return y;  
}  
```  
  
 在本情况下，编译器用 `si` 信息来访问 **static** 函数，而不需要用类的实例来调用 **static** 函数；所以发出警告。  若要解析该警告，您可以：  
  
-   添加一个构造函数，在该构造函数中编译器将使用 `si` 的实例来调用 `func`。  
  
-   从 `func` 定义中移除 **static** 关键字。  
  
-   显式调用 **static** 函数：`int y = S::func();`。