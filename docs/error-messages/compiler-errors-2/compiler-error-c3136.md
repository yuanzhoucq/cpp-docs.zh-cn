---
title: "编译器错误 C3136 | Microsoft Docs"
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
  - "C3136"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3136"
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3136
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“interface”: COM 接口只能从另一个 COM 接口继承，“interface”不是 COM 接口  
  
 您对其应用[接口特性](../../windows/interface-attributes.md)的接口是从非 COM 接口的接口继承的。  COM 接口最终从 `IUnknown` 继承。  任何前面是接口特性的接口都是 COM 接口。  
  
 下面的示例生成 C3136：  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```