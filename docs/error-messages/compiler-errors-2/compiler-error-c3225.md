---
title: "编译器错误 C3225 | Microsoft Docs"
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
  - "C3225"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3225"
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3225
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“arg”的泛型类型参数不能是“type”，它必须是值类型或句柄类型  
  
 泛型类型参数不是正确类型。  
  
 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 不能使用本机类型实例化泛型类型。  下面的示例生成 C3225。  
  
```  
// C3225.cpp  
// compile with: /clr  
class A {};  
  
ref class B {};  
  
generic <class T>  
ref class C {};  
  
int main() {  
   C<A>^ c = gcnew C<A>;   // C3225  
   C<B^>^ c2 = gcnew C<B^>;   // OK  
}  
```  
  
## 示例  
 下面的示例使用 C\# 创建一个组件。  请注意，该约束指定泛型类型只能使用值类型进行实例化。  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## 示例  
 此示例使用 C\# 编写的组件，违反了 MyList 只能使用 <xref:System.Nullable> 以外的值类型进行实例化的约束。  下面的示例生成 C3225。  
  
```  
// C3225_c.cpp  
// compile with: /clr  
#using "C3225_b.dll"  
ref class A {};  
value class B {};  
int main() {  
   MyList<A> x;   // C3225  
   MyList<B> y;   // OK  
}  
```