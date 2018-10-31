---
title: 日期和时间
ms.date: 11/04/2016
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: dcb5ef9f21987e11608cfa29e77b24e96153e6b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459444"
---
# <a name="date-and-time"></a>日期和时间

MFC 支持多种不同的使用日期和时间。 这些方法包括：

- 通用时间类。 [CTime](../atl-mfc-shared/reference/ctime-class.md)并[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)类封装了大部分使用 ANSI 标准时间库，在时间中声明关联的功能。H.

- 支持的系统时钟。 使用 MFC 3.0 版，支持已添加到`CTime`对 Win32`SYSTEMTIME`和`FILETIME`数据类型。

- 支持自动化[日期数据类型](../atl-mfc-shared/date-type.md)。 日期支持日期、 时间和日期/时间值。 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)并[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)类封装了此功能。 它们适用于[COleVariant](../mfc/reference/colevariant-class.md)类使用自动化的支持。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [日期和时间：SYSTEMTIME 支持](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [日期和时间：自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)

- [日期和时间：数据库支持](../atl-mfc-shared/date-and-time-database-support.md)

## <a name="see-also"></a>请参阅

[概念](../mfc/mfc-concepts.md)<br/>
[常规 MFC 主题](../mfc/general-mfc-topics.md)

