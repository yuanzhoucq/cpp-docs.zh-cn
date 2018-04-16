---
title: "32 位 Windows 时间/日期格式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.time
dev_langs:
- C++
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20e812a1eca6e620e0c1847b6ea6a07b871a407d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="32-bit-windows-timedate-formats"></a>32 位 Windows 时间/日期格式
将无符号整数用作位域，单独存储文件时间和日期。 文件的时间和日期打包如下：  
  
### <a name="time"></a>时间  
  
|位位置：|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|  
|-------------------|-----------------------|---------------------------|-----------------------|  
|长度：|5|6|5|  
|内容:|小时|分钟|2 秒的增量|  
|取值范围：|0-23|0-59|2 秒间隔中的 0-29|  
  
### <a name="date"></a>日期  
  
|位位置：|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|  
|-------------------|-------------------------------|-------------------|-----------------------|  
|长度：|7|4|5|  
|内容:|年|月|天|  
|取值范围：|0-119|1-12|1-31|  
||（相对于 1980）|||  
  
## <a name="see-also"></a>请参阅  
 [全局常量](../c-runtime-library/global-constants.md)