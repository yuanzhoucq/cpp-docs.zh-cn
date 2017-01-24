---
title: "编译器错误 C3138 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3138"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3138"
ms.assetid: 364ee9e8-9358-410e-bd35-9c4a226a3753
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3138
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“interface”:“attribute”接口必须从 IDispatch 继承，或者从继承自 IDispatch 的接口继承  
  
 具有 [dual](../../windows/dual.md) 或 [dispinterface](../../windows/dispinterface.md) 特性的接口没有将 `IDispatch` 作为直接或间接的基接口。  
  
 下面的示例生成 C3138：  
  
```  
// C3138.cpp  
#include <unknwn.h>  
  
[ object, uuid("77ac9240-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyCustomInterface  
{  
   HRESULT mf1(void);  
};  
  
[ dispinterface, uuid("3536f8a0-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyDispInterface : IUnknown  
{  
   [id(1)] HRESULT mf2(void);  
};  
  
[ object, dual, uuid("34e90a10-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyDualInterface : IMyCustomInterface  // C3138 expected  
{  
   HRESULT mf3(void);  
};  
```