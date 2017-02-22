---
title: "编译器错误 C3463 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3463"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3463"
ms.assetid: 153efcc0-085c-4615-84ea-d22942618bdf
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3463
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：类型不允许出现在特性“implements”中  
  
 向 [implements](../../windows/implements-cpp.md) 特性传递了一个无效类型。 例如，可以传递一个接口到 `implements`，但不能将一个指针传递到一个接口。  
  
## 示例  
 以下示例生成 C3463。  
  
```  
// C3463.cpp // compile with: /c #include <windows.h> [object, uuid("00000000-0000-0000-0000-000000000001")] __interface X {}; typedef X* PX; [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=PX) ]   // C3463 // try the following line instead // [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=X) ] class CMyClass : public X {};  
```