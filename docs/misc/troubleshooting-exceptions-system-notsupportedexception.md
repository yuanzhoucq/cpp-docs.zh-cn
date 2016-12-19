---
title: "关于异常的疑难解答：System.NotSupportedException | Microsoft Docs"
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
  - "NotSupportedException 类"
ms.assetid: a214e851-ee0f-4bbd-9f72-8769046526f3
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.NotSupportedException
当调用的方法不受支持时，或者当尝试读取、搜索或写入不支持所调用的功能的流时，就会引发 <xref:System.NotSupportedException> 异常。  
  
## 相关提示  
 **检查以确保该方法是受支持的。**  
 有些方法在基类中不受支持，但是这些方法将在派生类中受到支持。 如果派生类只实现了其基类中的一部分方法，它将对不支持的方法引发 <xref:System.NotSupportedException> 异常。  
  
## 备注  
 当使用 [!INCLUDE[Compact](../misc/includes/compact_md.md)] 并对本机函数使用 P\/Invoke 时，如果出现以下情况，则会引发此异常：  
  
-   托管代码中的声明不正确。  
  
-   [!INCLUDE[Compact](../misc/includes/compact_md.md)] 不支持尝试执行的操作。  
  
-   DLL 名称在导出时难以分辨。  
  
-   在这样的情况下，请检查：  
  
-   任何违反 [!INCLUDE[Compact](../misc/includes/compact_md.md)] P\/Invoke 限制的行为。  
  
-   任何需要预分配内存的参数。 如果存在这种情况，应传递对现有变量的引用。  
  
-   导出的函数的名称正确。 这可以通过 DumpBin.exe 进行验证。  
  
-   您没有尝试传递过多的参数。  
  
## 请参阅  
 <xref:System.NotSupportedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)