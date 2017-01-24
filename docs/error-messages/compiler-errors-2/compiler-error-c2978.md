---
title: "编译器错误 C2978 | Microsoft Docs"
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
  - "C2978"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2978"
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2978
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误：应为“keyword1”或“keyword2”；却发现类型“keyword3”；泛型中不支持非类型参数  
  
 未正确声明泛型类。 有关更多信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C2978：  
  
```  
// C2978.cpp // compile with: /clr /c generic <ref class T>   // C2978 // try the following line instead // generic <typename T>   // OK ref class Utils { static void sort(T elems, size_t size); }; generic <int> // try the following line instead // generic <class T> ref class Utils2 { static void sort(T elems, size_t size); };  
```