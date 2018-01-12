---
title: "编译器错误 C3225 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3225
dev_langs: C++
helpviewer_keywords: C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c189e2f4a0af7363f5bb988c9911bd90eb72809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3225"></a>编译器错误 C3225
arg 的泛型类型参数不能是 type，它必须是值类型或句柄类型  
  
 泛型类型参数不是类型的正确。  
  
 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 无法实例化具有本机类型的泛型类型。 下面的示例生成 C3225。  
  
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
  
## <a name="example"></a>示例  
 下面的示例创建一个使用 C# 的组件。 请注意，该约束指定泛型类型仅使用值类型进行实例化。  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## <a name="example"></a>示例  
 此示例使用 C# 的创作组件，并且违反 MyList 只能约束而不使用值类型实例化<xref:System.Nullable>。 下面的示例生成 C3225。  
  
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