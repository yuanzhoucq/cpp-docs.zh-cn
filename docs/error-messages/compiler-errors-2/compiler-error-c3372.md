---
title: "编译器错误 C3372 | Microsoft Docs"
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
  - "C3372"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3372"
ms.assetid: 38ee39ed-03ff-4e6d-9104-f1977b96645d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3372
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必须至少为组件类的 "source" 特性指定 1 个接口  
  
 对于某些特性，必须将接口名称作为参数传递。  
  
 下面的示例生成 C3372：  
  
```  
// C3372.cpp #include <windows.h> [module(name="MyModule")]; [ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ] __interface IMyIface { HRESULT f1(); }; // to resolve, pass an interface name to the source attribute // for example, source(IMyIface) [ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), source, default(IMyIface) ] // C3372 class CMyClass { }; int main() { }  
```