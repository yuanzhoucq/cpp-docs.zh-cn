---
title: "编译器警告（等级 4）C4434 | Microsoft Docs"
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
  - "C4434"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4434"
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4434
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类构造函数必须具有专用可访问性；更改为专用访问  
  
 C4434 指出编译器更改了静态构造函数的可访问性。  静态构造函数必须具有专用可访问性，因为它们仅应由公共语言运行时调用。  欲了解更多信息，请参阅 [静态构造函数](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。  
  
## 示例  
 下面的示例生成 C4434。  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```