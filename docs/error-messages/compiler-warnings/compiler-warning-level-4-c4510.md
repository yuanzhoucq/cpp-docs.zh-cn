---
title: "编译器警告（等级 4）C4510 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4510"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4510"
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4510
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 未能生成默认构造函数  
  
 编译器无法为指定的类生成默认构造函数；未创建任何用户定义的构造函数。  您将无法创建此类型的对象。  
  
 有几种阻止编译器生成默认构造函数的情况，其中包括：  
  
-   常数数据成员。  
  
-   是引用的数据成员。  
  
 需要为初始化这些成员的类创建用户定义的默认构造函数。  
  
 下面的示例生成 C4510：  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```