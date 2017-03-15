---
title: "编译器错误 C3665 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3665"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3665"
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C3665
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“destructor”: 析构函数\/终结器上不允许使用重写说明符“keyword”  
  
 使用了在析构函数或终结器上不允许的关键字。  
  
 例如，无法在析构函数或终结器上请求一个新的槽。有关隐式本地化和显式本地化的更多信息，请参见[明确覆盖](../../windows/explicit-overrides-cpp-component-extensions.md) 和 [析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 下面的示例生成 C3665：  
  
```  
// C3665.cpp  
// compile with: /clr  
public ref struct R {  
   virtual ~R() { }  
   virtual void a() { }  
};  
  
public ref struct S : R {  
   virtual ~S() new {}   // C3665  
   virtual void a() new {}   // OK  
};  
```