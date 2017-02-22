---
title: "编译器警告（等级 1）C4997 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4997"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4997"
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4997
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：组件类不实现 COM 接口或伪接口  
  
 以 [coclass](../../windows/coclass.md) 特性标记的类不实现接口。  
  
 以下示例生成 C4997：  
  
```  
// C4997.cpp // compile with: /WX // to resolve this C4997, uncomment all code #include <objbase.h> [ object ] __interface I { HRESULT func(); }; [ coclass ] struct C /*: I*/ { /* HRESULT func() { return S_OK; } */ };   // C4997  
```