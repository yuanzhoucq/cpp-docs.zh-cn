---
title: "编译器警告（等级 4）C4682 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4682"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4682"
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4682
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“parameter”: 未指定方向参数特性，默认为 \[in\]  
  
 特性化接口中参数的方法不具有方向性特性：[in](../../windows/in-cpp.md) 或 [out](../../windows/out-cpp.md)。 参数默认为 in。  
  
 默认情况下，此警告处于关闭状态。 请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)了解详细信息。  
  
 下面的示例生成 C4682：  
  
```  
// C4682.cpp // compile with: /W4 #pragma warning(default : 4682) #include <windows.h> [module(name="MyModule")]; [ library_block, object, uuid("c54ad59d-d516-41dd-9acd-afda17565c2b") ] __interface IMyIface : IUnknown { HRESULT f1(int i, int *pi); // C4682 // try the following line // HRESULT f1([in] int i, [in] int *pi); }; int main() { }  
```