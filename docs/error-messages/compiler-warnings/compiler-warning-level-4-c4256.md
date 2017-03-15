---
title: "编译器警告（等级 4）C4256 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4256"
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 4）C4256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 带虚拟基的类的构造函数有“...”；调用可能与 Visual C\+\+ 的早期版本不兼容  
  
 可能为不兼容问题。  
  
 请考虑下面的代码示例。  如果构造函数的定义 S2::S2 \(int i，…\) 编译使用 Visual C\+\+ 编译器版本的在版本 7 之前，使用当前版本，而特定大小写的调用约定更改，但下面的示例进行编译，所以对构造函数的调用 S3 的不会正确工作。  如果两者都是用 Visual C\+\+ 6.0 编译的，调用也不会完全正常工作，除非不为省略号传递任何参数。  
  
 若要修复此警告，  
  
1.  不要在构造函数中使用省略号。  
  
2.  确保项目中的所有组件都用当前版本（包括任何可以定义或引用该类的库）生成，然后使用 [warning](../../preprocessor/warning.md) 杂注禁用此警告。  
  
 下面的示例生成 C4256：  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```