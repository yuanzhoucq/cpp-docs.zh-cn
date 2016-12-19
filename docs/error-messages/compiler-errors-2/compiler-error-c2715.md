---
title: "编译器错误 C2715 | Microsoft Docs"
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
  - "C2715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2715"
ms.assetid: c81567a7-5b65-468f-aaf9-835f91e468e4
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 无法引发或捕捉此类型  
  
 在托管代码中使用异常处理（请参见 [异常处理](../../windows/exception-handling-cpp-component-extensions.md) 了解更多信息）时，值类型不是有效参数。  
  
```  
// C2715a.cpp  
// compile with: /clr  
using namespace System;  
  
value struct V {  
   int i;  
};  
  
void f1() {  
   V v;  
   v.i = 10;  
   throw v;   // C2715  
   // try the following line instead  
   // throw ((V^)v);  
}  
  
int main() {  
   try {  
      f1();  
   }  
  
   catch(V v) { if ( v.i == 10 ) {   // C2715  
   // try the following line instead  
   // catch(V^ pv) { if ( pv->i == 10 ) {  
         Console::WriteLine("caught 10 - looks OK");  
      }   
      else {  
         Console::WriteLine("catch looks bad");  
      }  
   }  
   catch(...) {  
      Console::WriteLine("catch looks REALLY bad");  
   }  
}  
```  
  
 当在 C\+\+ 托管扩展中使用异常处理时，[\_\_value](../../misc/value.md) 类型或 [\_\_gc](../../misc/gc.md) 指针都是无效参数。  若要解决此错误，请使用 [\_\_box](../../misc/box.md) 关键字将该参数装箱。  
  
 下面的示例生成 C2715：  
  
```  
// C2715b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
  
__value struct V {  
   int i;  
};  
  
void f1() {  
   V v;  
   v.i = 10;  
   throw v;   // C2715  
   // try the following line instead  
   // throw __box(v);  
}  
  
int main() {  
   try {  
      f1();  
   }  
  
   catch(V v) { if ( v.i == 10 ) {   // C2715  
   // try the following line instead  
   // catch(__box V *pv) { if ( pv->i == 10 ) {  
         Console::WriteLine(S"caught 10 - looks OK");  
      }   
      else {  
         Console::WriteLine(S"catch looks bad");  
      }  
   }  
   catch(...) {  
      Console::WriteLine(S"catch looks REALLY bad");  
   }  
}  
```