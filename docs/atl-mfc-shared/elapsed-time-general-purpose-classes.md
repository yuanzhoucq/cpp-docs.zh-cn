---
title: 已用时间：通用类
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
ms.openlocfilehash: 5990f6f5db0270c8d24ff35b5c9bbea5b24e6ed7
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742046"
---
# <a name="elapsed-time-general-purpose-classes"></a>已用时间：通用类

下面的过程演示如何计算两个之间的差异`CTime`对象并获取`CTimeSpan`结果。 使用`CTime`和`CTimeSpan`对象来计算经过的时间，按如下所示：

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

一旦具有计算`elapsedTime`，可以使用的成员函数的`CTimeSpan`提取已用时间值的组件。
