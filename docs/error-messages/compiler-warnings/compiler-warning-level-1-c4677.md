---
title: "编译器警告（等级 1）C4677 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4677"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4677"
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器警告（等级 1）C4677
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 非私有成员的签名包含程序集私有类型“private\_type”  
  
 具有程序集外公共可访问性的类型使用在该程序集外具有私有访问权限的类型。  引用公共程序集类型的组件将无法使用引用程序集私有类型的类型成员。  
  
## 示例  
 下面的示例生成 C4677。  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```