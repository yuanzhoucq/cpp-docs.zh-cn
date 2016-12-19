---
title: "编译器警告 C4950 | Microsoft Docs"
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
  - "C4950"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4950"
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4950
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type\_or\_member”：标记为过时  
  
 使用 [ObsoleteAttribute](frlrfSystemObsoleteAttributeClassTopic) 将成员或类型标记为过时。  
  
 始终发出 C4950 错误。  可通过 `#pragma warning` 或 **\/wd** 关闭此警告；有关详细信息，请参阅[警告](../../preprocessor/warning.md)或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won（警告等级）](../../build/reference/compiler-option-warning-level.md)。  
  
 下面的示例生成 C4950：  
  
```  
// C4950.cpp // compile with: /clr using namespace System; // Any reference to Func3 should generate an error with message [System::ObsoleteAttribute("Will be removed in next version", true)] Int32 Func3(Int32 a, Int32 b) { return (a + b); } int main() { Int32 MyInt3 = ::Func3(2, 2);   // C4950 }  
```