---
title: "目录控制 | Microsoft Docs"
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
  - "c.programs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "控件 [C++], 目录"
  - "目录控制例程"
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 目录控制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些例程访问，修改，并获取有关目录结构的信息。  
  
### 目录控制例程  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_chdir、\_wchdir](../c-runtime-library/reference/chdir-wchdir.md)|改变当前的工作目录|[\<caps:sentence id\="tgt8" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_chdrive](../c-runtime-library/reference/chdrive.md)|更改当前驱动器|[\<caps:sentence id\="tgt11" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getcwd、\_wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|得到当前默认驱动器的工作目录|[\<caps:sentence id\="tgt14" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getdcwd、\_wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|得到当前指定驱动器的工作目录|[\<caps:sentence id\="tgt16" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|使用磁盘驱动器的信息对`_diskfree_t` 结构进行填充。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_getdrive](../c-runtime-library/reference/getdrive.md)|获得当前 \(默认\) 驱动器|[\<caps:sentence id\="tgt23" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getdrives](../c-runtime-library/reference/getdrives.md)|返回一个位掩码表示现在可用的磁盘驱动器。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mkdir、\_wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|创建新目录|[System::IO::Directory::CreateDirectory](https://msdn.microsoft.com/en-us/library/system.io.directory.createdirectory.aspx)，[System::IO::DirectoryInfo::CreateSubdirectory](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.createsubdirectory.aspx)|  
|[\_rmdir、\_wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|移除目录|[\<caps:sentence id\="tgt32" sentenceid\="de5c5e84e86fdd3cd99296d3b2518f57" class\="tgtSentence"\>System::IO::Directory::Delete\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.directory.delete.aspx)|  
|[\_searchenv、\_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [\_searchenv\_s、\_wsearchenv\_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|在特定文件中搜索指定路径|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [文件处理](../c-runtime-library/file-handling.md)   
 [系统调用](../c-runtime-library/system-calls.md)