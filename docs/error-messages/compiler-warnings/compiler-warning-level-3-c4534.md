---
title: "编译器警告（等级 3）C4534 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "c4534"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4534"
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 3）C4534
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由于默认参数，“constructor”将不是类“class”的默认构造函数  
  
 非托管类可以具有带默认参数值的构造函数，编译器将该构造函数用作默认构造函数。  用 `value` 关键字标记的类不会把带默认参数值的构造函数用作默认构造函数。  
  
 有关详细信息，请参阅[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下面的示例生成 C4534：  
  
```  
// C4534.cpp  
// compile with: /W3 /clr /WX  
value class MyClass {  
public:  
   int ii;  
   MyClass(int i = 9) {   // C4534, will not be the default constructor  
      i++;  
   }  
};  
  
int main() {  
   MyClass ^ xx = gcnew MyClass;  
   xx->ii = 0;  
}  
```