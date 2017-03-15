---
title: "编译器警告（等级 1）C4096 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4096"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4096"
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4096
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“a”: 接口不是 COM 接口；不发送到 IDL  
  
 要用作 COM 接口的接口定义未被定义为 COM 接口，因此不会将其发送到 IDL 文件。  
  
 有关指示接口为 COM 接口的列表特性，请参见[接口特性](../../windows/interface-attributes.md)。  
  
 下面的示例生成 C4096：  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```