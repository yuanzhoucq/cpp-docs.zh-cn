---
title: "运行时错误检查 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "运行时错误检查"
  - "运行时错误, 检查"
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 运行时错误检查
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 运行库包含支持运行时错误检查的函数 \(RTC\)。  运行时错误检查允许您生成程序的某些类型运行时错误报告。  指定如何报告错误，并且类型错误报告。  有关更多信息，请参见[运行时错误检查](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md)。  
  
 使用下列函数自定义项程序实现运行时错误检查的方式。  
  
### 启用运行时错误检查。  
  
|功能|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_RTC\_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|返回运行时错误检查 \(RTC\) 类型的简要描述。||  
|[\_RTC\_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|返回由运行时错误检查（RTC）发现的错误总数。||  
|[\_RTC\_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|指派一个函数作为报告运行时错误检查 \(RTC\) 的处理程序。||  
|[\_RTC\_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|关联由类型的运行时错误检查\(RTCs\)检测的错误。||  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [\/RTC（运行时错误检查）](../build/reference/rtc-run-time-error-checks.md)   
 [runtime\_checks](../preprocessor/runtime-checks.md)   
 [RTC sample](http://msdn.microsoft.com/zh-cn/b3415b09-f6fd-43dc-8c02-9a910bc2574e)   
 [调试例程](../c-runtime-library/debug-routines.md)