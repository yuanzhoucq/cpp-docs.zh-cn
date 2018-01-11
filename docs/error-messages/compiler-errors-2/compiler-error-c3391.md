---
title: "编译器错误 C3391 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3391
dev_langs: C++
helpviewer_keywords: C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5302939fa8a77a244c039d45c10ea5596897240
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3391"></a>编译器错误 C3391
type_arg： 必须是不可为 null 的值类型的泛型参数 param 泛型 generic_type 的类型参数无效。  
  
泛型类型实例化错误。 检查类型定义。 有关详细信息，请参阅<xref:System.Nullable>和[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
下面的示例使用 C# 来创建包含具有 C + 中创建泛型类型时，不支持某些约束的泛型类型的组件 + CLI。 有关详细信息，请参阅[类型参数的约束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。  
  
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