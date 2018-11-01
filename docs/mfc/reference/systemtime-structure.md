---
title: SYSTEMTIME 结构
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
ms.openlocfilehash: b46482a9f4eb0165b72d74cb7d69e96e2a15e953
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559037"
---
# <a name="systemtime-structure"></a>SYSTEMTIME 结构

`SYSTEMTIME`结构表示日期和时间使用单个成员的月、 天、 年、 工作日、 小时、 分钟、 秒和毫秒。

## <a name="syntax"></a>语法

```
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME;
```

#### <a name="parameters"></a>参数

*wYear*<br/>
当前年份。

*wMonth*<br/>
当前月;年 1 月为 1。

*wDayOfWeek*<br/>
当前日期是星期几;星期日为 0，星期一为 1，依此类推。

*wDay*<br/>
当前日期的月份。

*wHour*<br/>
在当前小时。

*wMinute*<br/>
当前分钟。

*wSecond*<br/>
当前秒。

*wMilliseconds*<br/>
当前毫秒。

## <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]

## <a name="requirements"></a>要求

**标头：** winbase.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

