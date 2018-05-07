---
title: 装箱值的跟踪句柄 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6d3be5a46eab68a7f02bb97c477c1ec0b7fcd54d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>装箱值的跟踪句柄
引用值类型的跟踪句柄的使用情况已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 装箱是统一的 CLR 类型系统的特性。 值类型的隐式对引用类型时直接包含它们的状态： 已命名的实体是托管堆上分配的未命名对象的句柄。 任何初始化或赋值值的类型转换为`Object`，例如，要求值类型放置在 CLR 堆-这是发生的映像的装箱它的第一次分配关联的内存，然后复制值类型的状态然后返回此匿名值/引用混合的地址。 因此，当编写以下代码在 C# 中  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 没有大得多的操作不是由代码的简单性变得非常明显。 C# 的设计隐藏不仅的操作都发生实质上，而且还要的抽象的装箱本身的复杂性。 托管扩展 c + +，另一方面，这会导致效率的 false 意义上，通过要求显式指令将其放置在用户的表面相关：  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 装箱是隐式 Visual c + +:  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 `__box`关键字作为一项重要服务内托管扩展中，一个不存在的设计中如 C# 和 Visual Basic 的语言： 它提供的词汇和跟踪句柄来直接操作托管堆上的已装箱的实例。 例如，请考虑以下的小程序：  
  
```  
int main() {  
   double result = 3.14159;  
   __box double * br = __box( result );  
  
   result = 2.7;   
   *br = 2.17;     
   Object * o = br;  
  
   Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
   Console::WriteLine( S"result :: {0}", __box(result) ) ;  
   Console::WriteLine( S"result :: {0}", br );  
}  
```  
  
 生成的三个调用的基础代码`WriteLine`显示访问装箱值的值的各种成本 （得益于 Yves Dolce 指出这些差异)，键入，其中指出的行显示与每个关联的开销调用。  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
call       void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", __box(result) ) ;  
Ldstr    " result :: {0}"  
ldloc.0  
box    [mscorlib]System.Double // box overhead  
call    void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", br );  
ldstr    "result :: {0}"  
ldloc.0  
call     void [mscorlib]System.Console::WriteLine(string, object)  
```  
  
 装箱的值类型将直接传递给`Console::WriteLine`消除了装箱和需要调用`ToString()`。 (当然，没有早期装箱初始化`br`，因此不会获得任何除非我们真正`br`工作。  
  
 在新语法中，对装箱的值类型的支持时显著更简洁且集成类型系统中保留其功能。 例如，下面是上述的小程序的转换：  
  
```  
int main()  
{  
   double result = 3.14159;  
   double^ br = result;  
   result = 2.7;  
   *br = 2.17;  
   Object^ o = br;  
   Console::WriteLine( "result :: {0}", result.ToString() );  
   Console::WriteLine( "result :: {0}", result );  
   Console::WriteLine( "result :: {0}", br );  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [值类型和它们的行为 (C + + /cli CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [如何：显式请求装箱](../dotnet/how-to-explicitly-request-boxing.md)