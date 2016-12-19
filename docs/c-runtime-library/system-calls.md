---
title: "系统调用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.system"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "系统调用"
  - "Windows [C++], 系统调用"
ms.assetid: 0255f2ec-a5a0-487e-8b09-9dad001d81ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 系统调用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下函数是 Windows 操作系统调用。  
  
### 系统调用函数  
  
|功能|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_findclose](../c-runtime-library/reference/findclose.md)|来自前面查找操作的发布资源|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_findfirst, \_findfirst32, \_findfirst64, \_findfirsti64, \_findfirst32i64, \_findfirst64i32, \_wfindfirst, \_wfindfirst32, \_wfindfirst64, \_wfindfirsti64, \_wfindfirst32i64, \_wfindfirst64i32](../c-runtime-library/reference/findfirst-functions.md)|找到具有指定特性的文件|[\<caps:sentence id\="tgt12" sentenceid\="e22cfa910fbeac637b6aba4ed3f9dc48" class\="tgtSentence"\>System::IO::DirectoryInfo::GetFiles\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)|  
|[\_findnext, \_findnext32, \_findnext64, \_findnexti64, \_findnext32i64, \_findnext64i32, \_wfindnext, \_wfindnext32, \_wfindnexti64, \_wfindnext64, \_wfindnexti64](../c-runtime-library/reference/findnext-functions.md)|找到下一个具有指定特性的文件|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [文件处理](../c-runtime-library/file-handling.md)   
 [目录控制](../c-runtime-library/directory-control.md)   
 [低级别 I\/O](../c-runtime-library/low-level-i-o.md)