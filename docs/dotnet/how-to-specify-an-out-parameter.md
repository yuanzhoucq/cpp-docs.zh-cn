---
title: "如何：指定 out 参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数参数"
  - "out 参数"
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：指定 out 参数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此示例演示如何将函数参数指定为 out 参数，以及如何从 C\# 程序中调用该函数。  
  
 在 Visual C\+\+ 中使用 <xref:System.Runtime.InteropServices.OutAttribute> 指定输出参数。  
  
## 示例  
 此示例的第一部分是一个 Visual C\+\+ DLL，其类型包含一个具有输出参数的函数。  
  
```  
// cpp_out_param.cpp  
// compile with: /LD /clr:safe  
using namespace System;  
public value struct TestStruct {  
   static void Test([Runtime::InteropServices::Out] String^ %s) {  
      s = "a string";  
   }  
};  
```  
  
## 示例  
 这是一个 C\# 客户端，它将使用前面示例中创建的 Visual C\+\+ 组件。  
  
```  
// cpp_out_param_2.cs  
// compile with: /reference:cpp_out_param.dll  
using System;  
class TestClass {  
   public static void Main() {  
      String t;  
      TestStruct.Test(out t);  
      System.Console.WriteLine(t);  
   }  
}  
```  
  
  **字符串**   
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)