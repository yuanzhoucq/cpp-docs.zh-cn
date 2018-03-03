---
title: "如何： 通过泛型 （Visual c + +） 提高性能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- performance, C++
- Visual C++, performance
- Visual C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d8aad77236e5c1b2cdc8fe5958d87d8c53b8f05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-improve-performance-with-generics-visual-c"></a>如何：通过泛型提高性能 (Visual C++)
采用泛型可以根据类型参数创建可重用的代码。 类型参数的实际类型将推迟，直到由客户端代码调用。 有关泛型的详细信息，请参阅[泛型](../windows/generics-cpp-component-extensions.md)。  
  
 本文讨论泛型如何有助于提高使用集合的应用程序的性能。  
  
## <a name="example"></a>示例  
 .NET Framework 在 <xref:System.Collections?displayProperty=fullName> 命名空间中附带了许多集合类。 这些集合大多数作用于 <xref:System.Object?displayProperty=fullName> 类型的对象。 这允许集合存储任何类型，因为 .NET Framework 中的所有类型（甚至是值类型）都派生自 <xref:System.Object?displayProperty=fullName>。 但是，此方法有两个缺点。  
  
 首先，如果集合存储值类型（如整型），值必须在添加到集合之前装箱，然后在从集合中检索时取消装箱。 这些操作开销很大。  
  
 其次，无法控制哪些类型可添加到集合。 将整数和字符串添加到同一集合是完全合法的，即使这可能不是所期望的。 因此，为了使代码的类型安全，必须检查从集合检索的类型确实是预期类型。  
  
 下面的代码示例显示了在采用泛型之前 .NET Framework 集合的两个主要缺点。  
  
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
  
```Output  
Popped a String: Seven  
Popped an int: 7  
```  
  
## <a name="example"></a>示例  
 新的 <xref:System.Collections.Generic?displayProperty=fullName> 命名空间包含在 <xref:System.Collections?displayProperty=fullName> 命名空间中找到的许多相同集合，但是它们已经修改以接受泛型类型参数。 这消除了非泛型集合的两个缺点：值类型装箱和取消装箱及无法指定集合中存储的类型。 对两个集合的操作相同；唯一区别在于实例化方式不同。  
  
 比较上述示例与使用泛型 <xref:System.Collections.Generic.Stack%601> 集合的此示例。 在访问频繁的大型集合中，此示例的性能显著高于前一个实例。  
  
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
  
```Output  
14  
```  
  
## <a name="see-also"></a>请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)