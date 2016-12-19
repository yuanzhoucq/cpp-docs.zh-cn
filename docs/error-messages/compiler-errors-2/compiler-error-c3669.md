---
title: "编译器错误 C3669 | Microsoft Docs"
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
  - "C3669"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3669"
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3669
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 重写说明符“override”不允许在静态成员函数或构造函数上使用  
  
 未正确指定重写。  有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3669。  
  
```  
// C3669.cpp  
// compile with: /clr  
public ref struct R {  
   R() override {}   // C3669  
};  
```