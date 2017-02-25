---
title: "编译器错误 C3836 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3836"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3836"
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3836
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

静态构造函数不允许有成员初始值设定项列表  
  
 托管类中不能有本身有成员初始化列表的静态构造函数。  公共语言运行时调用静态类构造函数进行类初始化，初始化静态数据成员。  
  
 下面的示例生成 C3836：  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
 下面的示例生成 C3836：  
  
```  
// C3836b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```