---
title: "编译器错误 C3269 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3269"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3269"
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3269
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 不能使用“...”声明托管或 WinRT 类型成员函数  
  
 托管和 WinRT 类成员函数不能声明可变长度的参数列表。  
  
 下面的示例将生成 C3269，并演示如何修复此错误：  
  
```  
// C3269_2.cpp  
// compile with: /clr  
  
ref struct A  
{  
   void func(int i, ...)   // C3269  
   // try the following line instead  
   // void func(int i )  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
 下面的示例将生成 C3269，并演示如何修复此错误：  
  
```  
// C3269.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc struct A  
{  
   void func(int i, ...)   // C3269  
   // try the following line instead  
   // void func(int i )  
   {  
   }  
};  
  
int main()  
{  
}  
```