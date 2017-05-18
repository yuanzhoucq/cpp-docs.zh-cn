---
title: "编译器错误 C3391 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3391
dev_langs:
- C++
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: 7b5922ccf353162dc32c99e3818227639d0f5985
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3391"></a>编译器错误 C3391
type_arg': 无效的类型参数的泛型参数 param 泛型 generic_type 必须是不可为 null 的值类型  
  
泛型类型实例化错误。 检查类型定义。 有关详细信息，请参阅<xref:System.Nullable>和[泛型](../../windows/generics-cpp-component-extensions.md)。</xref:System.Nullable>  
  
## <a name="example"></a>示例  
下面的示例使用 C# 来创建包含具有创作在 C + 的泛型类型时，不支持某些约束的泛型类型的组件 + CLI。 有关详细信息，请参阅[类型参数的约束](/dotnet/articles/csharp/programming-guide/generics/constraints-on-type-parameters)。  
  
```cs  
// C3391.cs  
// Compile by using: csc /target:library C3391.cs  
// a C# program  
public class GR<N>  
where N : struct {}  
```  
  
可用 C3391.dll 组件时，下面的示例生成 C3391。  
  
```cpp  
// C3391_b.cpp  
// Compile by using: cl /clr C3391_b.cpp  
#using <C3391.dll>  
using namespace System;  
value class VClass {};  
  
int main() {  
   GR< Nullable<VClass> >^ a =   
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable  
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK  
}  
```
