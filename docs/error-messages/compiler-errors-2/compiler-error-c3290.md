---
title: "编译器错误 C3290 | Microsoft Docs"
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
  - "C3290"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3290"
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3290
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 普通属性不能具有引用类型  
  
 未正确声明属性。 当声明普通属性时，编译器创建一个此属性将更新的变量，类中不能有跟踪引用变量。  
  
 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)和[% \(跟踪引用\)](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3290。  
  
```  
// C3290.cpp // compile with: /clr /c ref struct R {}; ref struct X { R^ mr; property R % y;   // C3290 property R ^ x;   // OK // OK property R% prop { R% get() { return *mr; } void set(R%) {} } }; int main() { X x; R% xp = x.prop; }  
```