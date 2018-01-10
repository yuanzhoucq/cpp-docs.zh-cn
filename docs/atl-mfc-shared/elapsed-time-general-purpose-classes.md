---
title: "运行时间： 的通用类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51eea60669fb7ad35525d65013ffc8420649349b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="elapsed-time-general-purpose-classes"></a>运行时间： 的通用类
下面的过程演示如何计算两个区别`CTime`对象和 get`CTimeSpan`结果。  
  
#### <a name="to-calculate-elapsed-time"></a>若要计算经过的时间  
  
1.  使用`CTime`和`CTimeSpan`对象以计算经过的时间，，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     一旦你计算`elapsedTime`，您可以使用成员函数的`CTimeSpan`提取已用时间值的组件。  
  
## <a name="see-also"></a>请参阅  
 [日期和时间：通用类](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

