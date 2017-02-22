---
title: "编译器错误 C3797 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3797"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3797"
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器错误 C3797
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“override”: 事件声明不能具有重写说明符\(而应将该说明符放在事件的 add\/remove\/raise 方法上\)  
  
 不能通过一个常用事件重写另一个常用事件（不具有显式定义的访问器方法的事件）。  进行重写的事件必须通过访问器函数定义其行为。  
  
 有关详细信息，请参阅[event](../../windows/event-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3797。  
  
```  
// C3797.cpp  
// compile with: /clr /c  
delegate void MyDel();  
  
ref class Class1 {  
public:  
   virtual event MyDel ^ E;  
};  
  
ref class Class2 : public Class1 {  
public:  
   virtual event MyDel ^ E override;   // C3797  
};  
  
// OK  
ref class Class3 : public Class1 {  
public:  
   virtual event MyDel ^ E {  
      void add(MyDel ^ d) override {}  
      void remove(MyDel ^ d) override {}  
   }  
};  
```