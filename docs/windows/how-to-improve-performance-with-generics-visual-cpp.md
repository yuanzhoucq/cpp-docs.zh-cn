---
title: "如何:增强与普通性能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "普通 [C++], 性能"
  - "性能, C++"
  - "Visual C++, 泛型"
  - "Visual C++, 性能"
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何:增强与普通性能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

泛型，可以创建根据类型参数的可重用的代码。  类型参数的实际类型将延迟到调用由客户端代码。  有关泛型的更多信息，请参见 [泛型](../windows/generics-cpp-component-extensions.md)。  
  
 本文讨论泛型如何有助于提高使用收集应用程序的性能。  
  
## 示例  
 .NET Framework 附带了 <xref:System.Collections?displayProperty=fullName> 命名空间的许多集合类中。  大多数这些集合都在类型为 <xref:System.Object?displayProperty=fullName>的对象。  这允许集合存储任何类型，因为所有 .NET Framework，即使值类型，它从 <xref:System.Object?displayProperty=fullName>派生。  但是，具有两个缺点在此方法。  
  
 首先，如果集合存储值类型，如整型，必须在添加到集合之前装箱值和未装箱，该值从集合中检索。  这些是开销大的操作。  
  
 接下来，无法控制哪些类型可添加到集合。  它完全是合法的加法整数和字符串到同一集合，因此，即使这可能不是所期望的。  因此，为了使代码可以为类型安全，必须检查从集合检索的类型实际上是预期内容的。  
  
 下面的代码示例在泛型之前显示 .NET Framework 集合的两个主要的缺点。  
  
```  
// perf_pre_generics.cpp  
// compile with: /clr  
  
using namespace System;  
using namespace System::Collections;  
  
int main()  
{  
    // This Stack can contain any type.  
    Stack ^s = gcnew Stack();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
  
    // Push a String to the same Stack.  
    // The Stack now contains two different data types.  
    s->Push("Seven");  
  
    // Pop the items off the Stack.  
    // The item is returned as an Object, so a cast is  
    // necessary to convert it to its proper type.  
    while (s->Count > 0)  
    {  
        Object ^o = s->Pop();  
        if (o->GetType() == Type::GetType("System.String"))  
        {  
            Console::WriteLine("Popped a String: {0}", (String ^)o);  
        }  
        else if (o->GetType() == Type::GetType("System.Int32"))  
        {  
            Console::WriteLine("Popped an int: {0}", (int)o);  
        }  
        else  
        {  
            Console::WriteLine("Popped an unknown type!");  
        }  
    }  
}  
```  
  
  **弹出字符串：七**  
**弹出一：7**   
## 示例  
 新的 <xref:System.Collections.Generic?displayProperty=fullName> 命名空间包含在 <xref:System.Collections?displayProperty=fullName> 命名空间中找到的许多相同的集合，但是，修改它们接受泛型类型参数。  这消除非泛型集合两个缺点：值类型装箱和取消装箱和无法指定集合中将存储的类型。  对两个集合的操作相同；而是在它们自己唯一区别在于如何实例化。  
  
 比较上面编写示例使用泛型集合 <xref:System.Collections.Generic.Stack%601> 的此示例。  在访问最频繁的大型集合，此示例的性能比前一个实例比大。  
  
```  
// perf_post_generics.cpp  
// compile with: /clr  
  
#using <System.dll>  
  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main()  
{  
    // This Stack can only contain integers.  
    Stack<int> ^s = gcnew Stack<int>();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
    s->Push(14);  
  
    // You can no longer push a String to the same Stack.  
    // This will result in compile time error C2664.  
    //s->Push("Seven");  
  
    // Pop an item off the Stack.  
    // The item is returned as the type of the collection, so no  
    // casting is necessary and no unboxing is performed for  
    // value types.  
    int i = s->Pop();  
    Console::WriteLine(i);  
  
    // You can no longer retrieve a String from the Stack.  
    // This will result in compile time error C2440.  
    //String ^str = s->Pop();  
}  
```  
  
  **14**   
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)