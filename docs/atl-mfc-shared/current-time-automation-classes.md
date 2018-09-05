---
title: 当前时间： 自动化类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9f267653f87ffcaf357a20abd5d72fd148d7900
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753430"
---
# <a name="current-time-automation-classes"></a>当前时间： 自动化类

下面的过程演示如何创建`COleDateTime`对象并将其初始化与当前时间。

#### <a name="to-get-the-current-time"></a>若要获取当前时间

1. 创建 `COleDateTime` 对象。

2. 调用 `GetCurrentTime`。

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>请参阅

[日期和时间：自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)

