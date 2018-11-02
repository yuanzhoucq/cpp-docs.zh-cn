---
title: 当前时间： 自动化类
ms.date: 11/04/2016
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
ms.openlocfilehash: 97984376057462daaebbf949e96131e91928a1ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596565"
---
# <a name="current-time-automation-classes"></a>当前时间： 自动化类

下面的过程演示如何创建`COleDateTime`对象并将其初始化与当前时间。

## <a name="to-get-the-current-time"></a>若要获取当前时间

1. 创建 `COleDateTime` 对象。

1. 调用 `GetCurrentTime`。

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>请参阅

[日期和时间：自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)
