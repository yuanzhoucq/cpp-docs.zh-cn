---
title: 日期和时间： SYSTEMTIME 支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecbfd517a0fd535a23920ae21d03f1756babc113
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="date-and-time-systemtime-support"></a>日期和时间： SYSTEMTIME 支持
[CTime](../atl-mfc-shared/reference/ctime-class.md)类具有构造函数接受从 Win32 的系统和文件时间。 如果你将 `CTime` 对象用于这些目的，你必须相应地修改它们的初始化，如本文所述。  
  
 有关 SYSTEMTIME 结构的信息，请参阅[SYSTEMTIME](../mfc/reference/systemtime-structure1.md)。 有关 FILETIME 结构的信息，请参阅[FILETIME](../mfc/reference/filetime-structure.md)。  
  
 MFC 仍然提供采用 MS-DOS 样式的时间参数的 `CTime` 构造函数，但是，从 MFC 版本 3.0 开始，`CTime` 类还支持采用 Win32 `SYSTEMTIME` 结构的构造函数和另一个采用 Win32 `FILETIME` 结构的构造函数。  
  
 新的 `CTime` 构造函数是：  
  
-   CTime (const SYSTEMTIME & `sysTime`);  
  
-   CTime (const FILETIME & `fileTime`);  
  
 `fileTime` 参数是对 Win32 `FILETIME` 结构的引用，此结构将时间表示为 64 位值，这是比 `SYSTEMTIME` 结构和 Win32 所使用的格式更便利的内部存储格式。  
  
 如果你的代码包含使用系统时间初始化的 `CTime` 对象，你应该使用 Win32 中的 `SYSTEMTIME` 构造函数。  
  
 你最有可能将不会使用`CTime``FILETIME`直接初始化。 如果你使用`CFile`对象操作文件， [cfile:: Getstatus](../mfc/reference/cfile-class.md#getstatus)为你通过检索文件时间戳`CTime`使用初始化对象`FILETIME`结构。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [常规日期和时间编程 MFC 中](../atl-mfc-shared/date-and-time.md)  
  
-   [日期和时间编程的自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [日期和时间编程的通用类](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>请参阅  
 [日期和时间](../atl-mfc-shared/date-and-time.md)

