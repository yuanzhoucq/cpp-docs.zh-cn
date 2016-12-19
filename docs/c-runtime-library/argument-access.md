---
title: "参数访问 | Microsoft Docs"
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
  - "c.arguments"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "参数访问宏 [C++]"
  - "变长参数列表"
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 参数访问
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当参数个数可变时，`va_arg`、`va_end`和 `va_start` 宏提供对函数参数的访问。  这些宏在为 ANSI C 兼容性定义在 STDARG.H 并且为 UNIX 系统 v 的兼容性定义在 VARARGS.H。  
  
### 参数\-访问宏  
  
|宏|使用|.NET Framework 等效项|  
|-------|--------|------------------------|  
|[va\_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|从列表中检索参数|[\<caps:sentence id\="tgt9" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
|[va\_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|重置指针|[\<caps:sentence id\="tgt12" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
|[va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|设置指向参数列表开始位置的指针|[\<caps:sentence id\="tgt15" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)