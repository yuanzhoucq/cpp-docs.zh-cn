---
title: "编译器警告（等级 4）C4564 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4564"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4564"
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 4）C4564
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类“class”的方法“method”定义不受支持的默认参数“parameter”  
  
 编译器检测到方法有一个或多个带默认值的参数。  调用该方法时将忽略参数的默认值；请显式指定这些参数的值。  如果不显式指定这些参数的值，C\+\+ 编译器将生成错误。  
  
 假设有下列用 Visual Basic 创建的 .dll，它允许方法参数上的默认参数：  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 以及有下列 C\+\+ 示例，它使用通过 Visual Basic 创建的 .dll。  
  
```  
// C4564.cpp  
// compile with: /clr /W4 /WX  
#using <C4564.dll>  
  
int main() {  
   TestClass ^ myx = gcnew TestClass();   // C4564  
   myx->MyMethod(9);  
   // try the following line instead, to avoid an error  
   // myx->MyMethod(9, 1);  
}  
```