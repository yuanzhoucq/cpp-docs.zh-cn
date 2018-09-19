---
title: 格式化时间值： 通用类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- dates, calculating intervals
- elapsed time, string representation
- time [C++], formatting
- formatting [C++], time
ms.assetid: 7fcfee24-f874-4a4d-95b3-adc19a0f2df0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8d61c845a059619e135dd07bc40a33ace046937
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759556"
---
# <a name="formatting-time-values-general-purpose-classes"></a>格式化时间值： 通用类

以下过程说明如何设置时间值的格式。

#### <a name="to-format-a-string-representation-of-a-time-or-elapsed-time"></a>若要设置格式的时间或时间的字符串表示形式

使用`Format`从成员函数[CTime](../atl-mfc-shared/reference/ctime-class.md)或[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)类来创建一个字符的字符串表示形式的时间或经过的时间，如以下示例所示。

   [!code-cpp[NVC_ATLMFC_Utilities#175](../atl-mfc-shared/codesnippet/cpp/formatting-time-values-general-purpose-classes_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [常规日期和时间编程 MFC 中](../atl-mfc-shared/date-and-time.md)

- [使用 SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [自动化的日期和时间编程的支持](../atl-mfc-shared/date-and-time-automation-support.md)

