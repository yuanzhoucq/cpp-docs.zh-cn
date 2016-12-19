---
title: "关于异常的疑难解答：System.FormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "FormatException 类"
ms.assetid: b2a4f55e-da87-4915-a053-59eb1595993d
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.FormatException
当实参的格式不符合分析类型或设置类型格式的方法的形参规范时，该方法会引发 <xref:System.FormatException> 异常。  
  
## 本文内容  
  
## 引发格式异常  
  
### 格式设置  
 *“格式”*是将类、结构或枚举值转换为它们的字符串表示形式的过程，通常是为了使得到的字符串可对用户显示或可用于保存对象的状态。  
  
 例如，<xref:System.Int32.ToString%28System.String%29?displayProperty=fullName> 采用字符串参数，此参数定义标准或自定义*“格式字符串”*，并返回数字的字符串表示形式。 如果格式字符串无效或不受支持，该方法将引发 <xref:System.FormatException>。  
  
### 复合格式设置  
 *“复合格式”*采用对象列表和复合格式字符串作为输入。 复合格式字符串由固定文本和索引占位符混和组成，其中索引占位符称为格式项，对应于列表中的对象。 格式设置操作产生的结果字符串由原始固定文本和列表中对象的字符串表示形式混和组成。  
  
 <xref:System.String.Format%2A?displayProperty=fullName> 和 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 是执行复合格式的方法示例。 如果格式字符串无效或格式项的索引小于零，或大于或等于参数的数目，使用复合格式的方法将引发 <xref:System.FormatException>。  
  
### 分析  
 *“分析”*是将表示 .NET Framework 基类的字符串转换为该基类的过程。 例如，分析操作用于将字符串转换为浮点数字或日期和时间值。  
  
 例如，<xref:System.Int32.Parse%28System.String%29?displayProperty=fullName><xref:System.DateTime.Parse%2A> 使用 <xref:System.IformatProvider> 参数中指定的区域性特定格式信息将日期和时间的字符串表示形式转换为与它等效的 <xref:System.DateTime>。 如果字符串格式不正确，将引发 <xref:System.FormatException>。  
  
## 避免 FormatExceptions  
 <xref:System.FormatException> 类引用文章包括 <xref:System.FormatException> 错误的常见原因和解决方案。  
  
 MSDN 库的 [格式化类型](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md) 和 [分析字符串](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md) 节包含有关正确设置类型格式和分析类型的信息。  
  
 **复合格式设置**  
  
 [复合格式设置](../Topic/Composite%20Formatting.md)  
  
 **数值类型**  
  
|||  
|-|-|  
|[标准数字格式字符串](../Topic/Standard%20Numeric%20Format%20Strings.md)|[自定义数字格式字符串](../Topic/Custom%20Numeric%20Format%20Strings.md)|  
|[分析数值字符串](../Topic/Parsing%20Numeric%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **日期和时间以及时间间隔类型**  
  
|||  
|-|-|  
|[标准日期和时间格式字符串](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)|[自定义日期和时间格式字符串](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)|  
|[标准 TimeSpan 格式字符串](../Topic/Standard%20TimeSpan%20Format%20Strings.md)|[自定义的 TimeSpan 格式字符串](../Topic/Custom%20TimeSpan%20Format%20Strings.md)|  
|[分析日期和时间字符串](../Topic/Parsing%20Date%20and%20Time%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **其他类型**  
  
|||  
|-|-|  
|[枚举格式字符串](../Topic/Enumeration%20Format%20Strings.md)|[分析其他字符串](../Topic/Parsing%20Other%20Strings%20in%20the%20.NET%20Framework.md)|