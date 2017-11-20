---
title: "运行时间： 自动化类 |Microsoft 文档"
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
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 51479f73112ed80ee981f3919fd3941d1eb0c8f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="elapsed-time-automation-classes"></a>运行时间： 自动化类
此过程演示如何计算两个区别`CTime`对象和 get`CTimeSpan`结果。  
  
#### <a name="to-calculate-elapsed-time"></a>若要计算经过的时间  
  
1.  创建两个`COleDateTime`对象。  
  
2.  设置之一`COleDateTime`为当前时间的对象。  
  
3.  执行某些耗时的任务。  
  
4.  设置其他`COleDateTime`为当前时间的对象。  
  
5.  需要两次时间之间的差异。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [日期和时间：自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)

