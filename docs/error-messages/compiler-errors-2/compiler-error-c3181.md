---
title: "编译器错误 C3181 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3181"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3181"
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3181
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 运算符的操作数无效  
  
 向 [\_\_typeof](../../misc/typeof.md) 或 [typeid](../../windows/typeid-cpp-component-extensions.md) 运算符传递了无效的参数。  该参数必须是托管类型。  
  
 请注意，编译器使用映射到公共语言运行时中类型的本机类型的别名。  
  
 下面的示例生成 C3181：  
  
```  
// C3181a.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181  
   Type ^pType2 = int::typeid;   // OK  
}  
```  
  
 下面的示例生成 C3181：  
  
```  
// C3181b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
int main() {  
   Type *pType1 = __typeof(int __gc*);   // C3181  
   Type *pType2 = __typeof(int*);   // OK  
}  
```