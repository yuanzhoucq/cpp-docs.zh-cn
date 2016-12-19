---
title: "SafeInt 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数, SafeInt"
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: 13
caps.handback.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

SafeInt 库提供可使用，而不创建 [SafeInt 类](../windows/safeint-class.md)实例的多个函数。  如果要防止整数溢出的个数学运算，则您可使用这些函数。  如果要保护多个数学运算，则应当创建 `SafeInt` 对象。  更高效一些创建 `SafeInt` 对象比使用这些函数多次。  
  
 这些函数使您能够比较或者对两种不同类型的参数的数学运算，而无需先将它们转换为相同类型。  
  
 这些函数中的每一模板有两种类型：`T` 和 `U`。  上述每个类型可以是布尔值、字符或整型。  整型可以带符号或无符号 8 位和从的任何范围为 64 位。  
  
## 本节内容  
  
|功能|说明|  
|--------|--------|  
|[SafeAdd](../windows/safeadd.md)|将两个数和溢出保护。|  
|[SafeCast](../windows/safecast.md)|将参数转换的一种类型到另一种类型的。|  
|[SafeDivide](../windows/safedivide.md)|将两个数相除并防止除以零。|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [SafeNotEquals](../windows/safenotequals.md)|比较两个数。  这些函数使您能够比较数的两种不同类型，不更改其类型。|  
|[SafeModulus](../windows/safemodulus.md)|对两个数相加的模数操作。|  
|[SafeMultiply](../windows/safemultiply.md)|一起乘以两个数字并保护溢出。|  
|[SafeSubtract](../windows/safesubtract.md)|两减去数字和溢出保护。|  
  
## 相关章节  
  
|节|说明|  
|-------|--------|  
|[SafeInt 类](../windows/safeint-class.md)|`SafeInt` 类。|  
|[SafeIntException 类](../windows/safeintexception-class.md)|到 SafeInt 库的类特定异常。|