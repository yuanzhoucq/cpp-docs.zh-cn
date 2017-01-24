---
title: "调用示例的结果 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "示例 [C++], 调用的结果"
  - "结果, __cdecl 调用"
  - "结果, __fastcall 关键字调用"
  - "结果, __stdcall 调用"
  - "结果, thiscall 调用"
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 调用示例的结果
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
  
## \_\_cdecl  
 C 修饰函数名为“\_MyFunc”。  
  
 ![CDECL 调用约定](../Image/vc37I01.gif "vc37I01")  
\_\_cdecl 调用约定  
  
## \_\_stdcall 和 thiscall  
 C 修饰名 \(`__stdcall`\) 是“\_MyFunc@20”。该 C \+\+ 修饰名是专用的。  
  
 ![&#95;&#95;stdcall 和 thiscall 调用约定](../cpp/media/vc37i02.png "vc37I02")  
\_\_stdcall 和 thiscall 调用约定  
  
## \_\_fastcall  
 C 修饰名 \(`__fastcall`\) 是“@MyFunc@20”。该 C \+\+ 修饰名是专用的。  
  
 ![&#95;&#95;fastcall 调用约定](../cpp/media/vc37i03.png "vc37I03")  
\_\_fastcall 调用约定  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)