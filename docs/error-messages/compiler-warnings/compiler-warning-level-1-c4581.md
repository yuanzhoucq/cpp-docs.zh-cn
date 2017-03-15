---
title: "编译器警告（等级 1）C4581 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4581"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4581"
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器警告（等级 1）C4581
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已否决的行为:“string1”替换为“string2”以处理特性  
  
 为 Visual C\+\+ 2005 执行的编译器一致性工作（Visual C\+\+ 特性的参数检查）可能导致此错误。  
  
 在以前的版本中，是否接受特性值要看它们是否括在引号内。  如果值是枚举，则它绝对不能括在引号内。  
  
## 示例  
 下面的示例生成 C4581。  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```