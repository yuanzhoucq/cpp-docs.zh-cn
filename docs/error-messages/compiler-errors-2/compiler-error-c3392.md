---
title: "编译器错误 C3392 | Microsoft Docs"
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
  - "C3392"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3392"
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3392
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type\_arg”: 对于泛型“generic\_type”，泛型参数“param”的类型变量无效，它必须具有公共无参数构造函数  
  
 泛型类型实例化错误。  检查类型定义。  有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 下面使用 C\# 的示例创建了一个包含泛型类型的组件，其此组件带有在 [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)] 中创建泛型类型时不受支持的部分约束。 有关详细信息，请参阅[类型参数的约束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
```  
// C3392.cs // compile with: /target:library // a C# program public class GR<C, V, N> where C : class where V : struct where N : new() {}  
```  
  
## 示例  
 以下示例生成 C3392。  
  
```  
// C3392_b.cpp // compile with: /clr #using <C3392.dll> ref class R { R(int) {} }; ref class N { N() {} }; value class V {}; ref class N2 { public: N2() {} }; ref class R2 { public: R2() {} }; int main () { GR<R^, V, N^>^ gr1;   // C3392 GR<R^, V, N2^>^ gr1a;   // OK GR<R^, N^, N^>^ gr3;   // C3392 GR<R^, V, N2^>^ gr3a;   // OK GR<R^, V, R^>^ gr4;   // C3392 GR<R^, V, R2^>^ gr4a;   // OK }  
```