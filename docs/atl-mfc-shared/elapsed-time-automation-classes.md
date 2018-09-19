---
title: 已用时间： 自动化类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcde08e8ffdb30f9ebf0ae7577bf836e84513a07
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751672"
---
# <a name="elapsed-time-automation-classes"></a>已用时间： 自动化类

此过程演示如何计算两个之间的差异`CTime`对象并获取`CTimeSpan`结果。

#### <a name="to-calculate-elapsed-time"></a>若要计算经过的时间

1. 创建两个`COleDateTime`对象。

2. 将一种设置`COleDateTime`为当前时间的对象。

3. 执行一些耗时的任务。

4. 设置其他`COleDateTime`为当前时间的对象。

5. 需要两个时间之间的差异。

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>请参阅

[日期和时间：自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)

