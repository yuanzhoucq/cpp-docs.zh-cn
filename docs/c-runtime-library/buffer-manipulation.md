---
title: "缓冲区操作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "缓冲区"
  - "缓冲区, 操作例程"
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 缓冲区操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用这些例程使用内存使用区域根据逐字节进行。  
  
### 缓冲区处理例程  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_memccpy](../c-runtime-library/reference/memccpy.md)|复制一缓冲区的字符。直到另一个特定字符或字符的多个副本|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)，[System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[memchr、wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|对第一次出现的返回指针，在字符内指定的编号，在缓冲区的特定字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[memcmp、wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|若要指定字符的数字从两缓冲区|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)，[System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy\_s、wmemcpy\_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|复制指定字符的数字从一缓冲区为另一种类型|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)，[System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[\_memicmp、\_memicmp\_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|若要指定字符的数字从两缓冲区而不考虑大小写|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)，[System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove\_s、wmemmove\_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|复制指定字符的数字从一缓冲区为另一种类型|[\<caps:sentence id\="tgt21" sentenceid\="3833f84fafc5c85a0cac972319a7142c" class\="tgtSentence"\>System::Buffer::BlockCopy\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)|  
|[memset、wmemset](../c-runtime-library/reference/memset-wmemset.md)|在缓冲区使用给定初始化字符指定的字节数。|[\<caps:sentence id\="tgt23" sentenceid\="b681ccb0db940e3c31a14bf4b7e7aaf8" class\="tgtSentence"\>System::Buffer::SetByte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.buffer.setbyte.aspx)|  
|[\_swab](../c-runtime-library/reference/swab.md)|交换字节数据并在指定位置中。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
 如果源和目标区域重叠，因此，只有 `memmove` 将确保正确复制全部源。  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)