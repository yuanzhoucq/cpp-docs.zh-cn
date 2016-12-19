---
title: "日期和时间︰ SYSTEMTIME 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "SYSTEMTIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "系统时间"
  - "FILETIME 结构，与 CTime 类"
  - "时间格式设置 [c + +]"
  - "SYSTEMTIME 结构"
  - "MFC 的日期 [c + +]"
  - "格式 [c + +]、 时间"
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 日期和时间︰ SYSTEMTIME 支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

 [CTime](../atl-mfc-shared/reference/ctime-class.md) 类有接受来自 Win32 的系统和文件时间的构造函数。 如果你将 `CTime` 对象用于这些目的，你必须相应地修改它们的初始化，如本文所述。  
  
 有关 SYSTEMTIME 结构的信息，请参阅 [SYSTEMTIME](../mfc/reference/systemtime-structure1.md)。 有关 FILETIME 结构的信息，请参阅 [FILETIME](../mfc/reference/filetime-structure.md)。  
  
 MFC 仍然提供采用 MS-DOS 样式的时间参数的 `CTime` 构造函数，但是，从 MFC 版本 3.0 开始，`CTime` 类还支持采用 Win32 `SYSTEMTIME` 结构的构造函数和另一个采用 Win32 `FILETIME` 结构的构造函数。  
  
 新的 `CTime` 构造函数是：  
  
-   CTime (const SYSTEMTIME & `sysTime`);  
  
-   CTime (const FILETIME & `fileTime`);  
  
 `fileTime` 参数是对 Win32 `FILETIME` 结构的引用，此结构将时间表示为 64 位值，这是比 `SYSTEMTIME` 结构和 Win32 所使用的格式更便利的内部存储格式。  
  
 如果你的代码包含使用系统时间初始化的 `CTime` 对象，你应该使用 Win32 中的 `SYSTEMTIME` 构造函数。  
  
 您最有可能不会使用 `CTime` `FILETIME` 直接初始化。 如果您使用 `CFile` 对象操作文件， [cfile:: Getstatus](../mfc/reference/cfile-class.md#getstatus) 为你通过检索文件时间戳 `CTime` 初始化对象， `FILETIME` 结构。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [常规日期和时间编程在 MFC 中](../atl-mfc-shared/date-and-time.md)  
  
-   [日期和时间编程的自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [日期和时间编程的通用类](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>另请参阅  
 [日期和时间](../atl-mfc-shared/date-and-time.md)

