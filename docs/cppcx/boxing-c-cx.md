---
title: "装箱 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
caps.latest.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 12
---
# 装箱 (C++/CX)
装箱就是当一个值类型变量（如 [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)）或基础标量类型（如 `int`）传递给以 [Platform::Object^](../cppcx/platform-object-class.md) 作为其输入类型的方法时，将该变量或类型包装在一个 ref 类中的过程。  
  
## 将值类型传递给 Object^ 参数  
 虽然无需显式装箱变量以将该其传递给类型 [Platform::Object^](../cppcx/platform-object-class.md) 的方法参数，但当你检索之前已装箱的值时，必须显式转换回原始类型。  
  
 [!code-cpp[cx_boxing#01](../snippets/cpp/VS_Snippets_Misc/cx_boxing/cpp/class1.cpp#01)]  
  
### 使用 Platform::IBox\<T\> 以支持可以为 null 的值类型  
 C\# 和 Visual Basic 支持可以为 null 的值类型的概念。 在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，可以使用 `Platform::IBox<T>` 类型以公开支持可以为 null 的值类型参数的公共方法。 下面的示例演示一个 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 公共方法，该方法在 C\# 调用方为某个参数传递 null 时返回 null。  
  
 [!code-cpp[cx_boxing#02](../snippets/cpp/VS_Snippets_Misc/cx_boxing/cpp/class1.h#02)]  
  
 在 C\# XAML 客户端中，可按以下方式使用它：  
  
```  
  
// C# client code BoxingDemo.Class1 obj = new BoxingDemo.Class1(); int? a = null; int? b = 5; var result = obj.Multiply(a,b); //result = null  
  
```  
  
## 请参阅  
 [类型系统 \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [强制转换 \(C\+\+\/CX\)](../cppcx/casting-c-cx.md)   
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)