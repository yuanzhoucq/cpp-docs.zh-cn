---
title: "steady_clock 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: chrono/std::chrono::steady_clock
dev_langs: C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5cd10ebcb9a068e78109c1a232b04c6beff9ebac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="steadyclock-struct"></a>steady_clock 结构
表示 `steady` 时钟。  
  
## <a name="syntax"></a>语法  
  
```  
struct steady_clock;  
```  
  
## <a name="remarks"></a>备注  
 在 Windows 上，steady_clock 会包装 QueryPerformanceCounter 函数。  
  
 如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为单调时钟。  
  
 如果它是单调时钟并且时钟计时周期之间的时间是常量，则为稳定时钟。  
  
 High_resolution_clock 是 steady_clock 的 typdef。  
  
## <a name="public-functions"></a>公共函数  
  
|函数|描述|  
|--------------|-----------------|  
|现在|返回当前时间作为 time_point 值。|  
  
## <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|`system_clock::is_steady`|保存 `true`。 `steady_clock` 是*稳定的*。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<chrono >  
  
 **命名空间：**std::chrono  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [system_clock 结构](../standard-library/system-clock-structure.md)
