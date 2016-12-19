---
title: "装箱值的跟踪句柄 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "装箱的值类型, 跟踪句柄"
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 装箱值的跟踪句柄
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，引用值类型的跟踪句柄的用法发生了更改。  
  
 装箱是 CLR 统一类型系统的特性。  值类型直接包含其状态，而引用类型则是隐式对：命名实体是托管堆上分配的未命名对象的句柄。  例如，值类型到 `Object` 的任何初始化或赋值要求该值类型放在 CLR 堆内（这是发生装箱的映像的位置）— 首先分配关联的内存，然后复制值类型的状态，最后返回此匿名值\/引用混合的地址。  这样，当使用 C\# 编写以下代码时，  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 其好处决不仅仅是代码的简洁性带来的明显性。  C\# 的设计不仅隐藏了后台发生的操作的复杂性，还隐藏了装箱本身的抽象化的复杂性。  另一方面，C\+\+ 托管扩展由于担心导致对效率的错误判断，所以要求用户编写显式指令：  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中，装箱是隐式的：  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 `__box` 关键字作为托管扩展中的一项重要服务，在诸如 C\# 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 的语言的设计中是没有的：它提供词汇和跟踪句柄来直接操作托管堆上的装箱实例。  例如，考虑以下小程序：  
  
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
  
 为 `WriteLine` 的三个调用生成的基础代码显示访问装箱值类型的值的各种代价（感谢 Yves Dolce 指出这些区别），其中指出的行显示与每个调用关联的系统开销。  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
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
  
 将装箱值类型直接传递给 `Console::WriteLine` 可以消除装箱和调用 `ToString()` 的需要。（当然，前面有对 `br` 的初始化装箱，所以除非我们真正使用 `br`，否则将不会获得任何结果。）  
  
 在新语法中，对装箱值类型的支持被认为是更佳的并且集成到了类型系统内部，同时保留其功能不变。  例如，下列代码是上述小程序的转换：  
  
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
  
## 请参阅  
 [值类型及其行为 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [如何：显式请求装箱](../dotnet/how-to-explicitly-request-boxing.md)