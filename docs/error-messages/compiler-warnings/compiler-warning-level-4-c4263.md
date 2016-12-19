---
title: "编译器警告（等级 4）C4263 | Microsoft Docs"
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
  - "C4263"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4263"
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4263
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 成员函数不重写任何基类虚拟成员函数  
  
 类函数定义与基类中的虚函数同名，但参数的数目或类型不同。  这有效地隐藏了基类中的虚函数。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4263：  
  
```  
// C4263.cpp  
// compile with: /W4  
#pragma warning(default:4263)  
#pragma warning(default:4264)  
class B {  
public:  
   virtual void func();  
};  
  
class D : public B {  
   void func(int);   // C4263  
};  
  
int main() {  
}  
```