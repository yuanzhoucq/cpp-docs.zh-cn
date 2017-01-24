---
title: "编译器警告（等级 4）C4681 | Microsoft Docs"
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
  - "C4681"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4681"
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4681
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：组件类不指定是事件源的默认接口  
  
 未为类指定[源](../../windows/source-cpp.md)接口。  
  
 下面的示例生成 C4681：  
  
```  
// C4681.cpp // compile with: /W4 /c #define _ATL_ATTRIBUTES 1 #include <atlbase.h> #include <atlcom.h> [module(name="test")]; [dual, uuid("00000000-0000-0000-0000-000000000000")] __interface IEvent { [id(3)] HRESULT myEvent(); }; [object, uuid("00000000-0000-0000-0000-000000000001")] __interface ISource { HRESULT Fire(); }; [ coclass, source(IEvent), default(ISource), // Uncomment the following line to resolve. // default(IEvent), uuid("00000000-0000-0000-0000-000000000002") ] struct CSource : ISource {   // C4681 HRESULT Fire() { return 0; } };  
```