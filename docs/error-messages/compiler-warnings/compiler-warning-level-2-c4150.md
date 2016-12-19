---
title: "编译器警告（等级 2）C4150 | Microsoft Docs"
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
  - "C4150"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4150"
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4150
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

删除指向不完整“type”类型的指针；没有调用析构函数  
  
 调用 **delete** 运算符来删除已声明但未定义的类型，这样编译器不能发现析构函数。  
  
 下面的示例生成 C4150：  
  
```  
// C4150.cpp  
// compile with: /W2  
class  IncClass;  
  
void NoDestruct( IncClass* pIncClass )  
{  
   delete pIncClass;  
} // C4150, define class to resolve  
  
int main()  
{  
}  
```