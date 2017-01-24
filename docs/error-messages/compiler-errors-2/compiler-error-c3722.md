---
title: "编译器错误 C3722 | Microsoft Docs"
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
  - "C3722"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3722"
ms.assetid: 3cb28363-5eff-4548-bd0d-d5c615846353
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3722
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许泛型事件  
  
 编译器只允许泛型类、结构和函数。有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
 下面的示例生成 C3722：  
  
```  
// C3722.cpp  
// compile with: /clr  
generic <typename T>  
public delegate void MyEventHandler(System::Object^ sender, System::EventArgs^ e, T optional);  
  
generic <class T>  
public ref struct MyButton {  
   generic<typename U>  
   event MyEventHandler<U>^ Click;   // C3722  
};  
```