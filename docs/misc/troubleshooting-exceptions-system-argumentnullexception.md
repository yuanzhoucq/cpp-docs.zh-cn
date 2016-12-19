---
title: "关于异常的疑难解答：System.ArgumentNullException | Microsoft Docs"
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
  - "ArgumentNullException 类"
ms.assetid: 5f21413c-d997-47c6-9b06-3d85a719d51b
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ArgumentNullException
如果向方法传递空引用（在 Visual Basic 中为 <xref:System.ArgumentNullException>），而该方法不接受空引用为有效参数，则会引发 `Nothing` 异常。  
  
## 相关提示  
 **检查参数以确保它们不为空（在 Visual Basic 中为 Nothing）。**  
 空引用是对不存在的对象的引用，原因通常是还未以编程方式创建该对象的任何实例。  
  
## 备注  
 <xref:System.ArgumentNullException> 的行为与 <xref:System.ArgumentException> 的行为相同。 提供它是为了使应用程序代码能够区分由空参数引发的异常和由非空参数引发的异常。 有关由非空参数引起的错误，请参见 [关于异常的疑难解答：System.ArgumentOutOfRangeException](../misc/troubleshooting-exceptions-system-argumentoutofrangeexception.md)。  
  
## 请参阅  
 <xref:System.ArgumentNullException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)