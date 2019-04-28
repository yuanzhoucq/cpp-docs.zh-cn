---
title: 格式化时间值：通用类
ms.date: 11/04/2016
helpviewer_keywords:
- dates, calculating intervals
- elapsed time, string representation
- time [C++], formatting
- formatting [C++], time
ms.assetid: 7fcfee24-f874-4a4d-95b3-adc19a0f2df0
ms.openlocfilehash: bab93638d81e8e4e5d6f7ce71bf6a3180fa7f7e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236393"
---
# <a name="formatting-time-values-general-purpose-classes"></a>格式化时间值：通用类

以下过程说明如何设置时间值的格式。

#### <a name="to-format-a-string-representation-of-a-time-or-elapsed-time"></a>若要设置格式的时间或时间的字符串表示形式

使用`Format`从成员函数[CTime](../atl-mfc-shared/reference/ctime-class.md)或[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)类来创建一个字符的字符串表示形式的时间或经过的时间，如以下示例所示。

   [!code-cpp[NVC_ATLMFC_Utilities#175](../atl-mfc-shared/codesnippet/cpp/formatting-time-values-general-purpose-classes_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [常规日期和时间编程 MFC 中](../atl-mfc-shared/date-and-time.md)

- [使用 SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [自动化的日期和时间编程的支持](../atl-mfc-shared/date-and-time-automation-support.md)
