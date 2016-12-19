---
title: "关于异常的疑难解答：System.MissingMemberException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "MissingMemberException 类"
ms.assetid: c4cf497b-0554-47fe-b2e9-81ee3eb9ec04
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.MissingMemberException
当尝试动态访问不存在的类成员时，会引发 <xref:System.MissingMemberException> 异常。  
  
## 相关提示  
 **如果类库中的某个成员已移除或重命名，请重新编译引用该库的所有程序集。**  
 当一个程序集中的某个字段或方法被删除或重命名，而这一更改未反映在另一个尝试访问这个丢失的成员的程序集中时，通常会引发此异常。  
  
 **如果您尝试访问后期绑定对象变量上的成员，请确保将该变量声明为“Public”。**  
 在 Visual Basic 中，`Protected`、`Friend` 和 `Private` 变量不能是后期绑定的。  
  
## 请参阅  
 <xref:System.MissingMemberException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)