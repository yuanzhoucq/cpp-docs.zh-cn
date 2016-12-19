---
title: "编译器错误 C3391 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3391"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3391"
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3391
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type\_arg”：对于泛型“generic\_type”的泛型形参“param”无效的类型实参必须是不可为 null 的值类型  
  
 泛型类型实例化错误。  检查类型定义。  有关详细信息，请参阅<xref:System.Nullable>和[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 下面使用 C\# 的示例创建了一个包含泛型类型的组件，其此组件带有在 [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)] 中创建泛型类型时不受支持的部分约束。 有关详细信息，请参阅[类型参数的约束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
```  
// C3391.cs // compile with: /target:library // a C# program public class GR<N> where N : struct {}  
```  
  
## 示例  
 以下示例生成 C3391。  
  
```  
// C3391_b.cpp // compile with: /clr #using <C3391.dll> using namespace System; value class VClass {}; int main() { GR< Nullable<VClass> >^ a = gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable GR<VClass>^ aa = gcnew GR<VClass>();   // OK }  
```