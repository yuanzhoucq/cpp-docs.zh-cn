---
title: "编译器错误 C3390 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3390"
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type\_arg”: 对于泛型“generic\_type”，泛型参数“param”的类型实参无效，它必须是引用类型  
  
 泛型类型实例化错误。  检查类型定义。  有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 下面使用 C\# 的示例创建了一个包含泛型类型的组件，其此组件带有在 [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)] 中创建泛型类型时不受支持的部分约束。 有关详细信息，请参阅[类型参数的约束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
```  
// C3390.cs // compile with: /target:library // a C# program public class GR<C, V, N> where C : class where V : struct where N : new() {}  
```  
  
## 示例  
 以下示例生成 C3390。  
  
```  
// C3390_b.cpp // compile with: /clr #using <C3390.dll> ref class R { R(int) {} }; value class V {}; ref struct N { N() {} }; int main () { GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type GR<R^, V, N^>^ gr2b;   // OK }  
```