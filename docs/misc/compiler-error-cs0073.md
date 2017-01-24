---
title: "编译器错误 CS0073 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0073"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0073"
ms.assetid: 579ae534-59ab-4fc5-ad7e-f87639f3f9cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0073
add 访问器或 remove 访问器必须有一个主体  
  
 [事件](../Topic/event%20\(C%23%20Reference\).md)定义中的 **add** 或 **remove** 关键字必须有一个主体。 有关详细信息，请参阅[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)。  
  
 以下示例生成 CS0073：  
  
```  
// CS0073.cs delegate void del(); class Test { public event del MyEvent { add;   // CS0073 // try the following lines instead // add // { //    MyEvent += value; // } remove { MyEvent -= value; } } public static void Main() { } }  
```