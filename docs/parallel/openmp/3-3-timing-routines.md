---
title: 3.3 计时例程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3b8fc16e34124419362d5989131c2cf66df30b6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="33-timing-routines"></a>3.3 计时例程
本部分中描述的功能支持的可移植的时钟计时器：  
  
-   `omp_get_wtime`函数将返回已用的时钟时间。  
  
-   `omp_get_wtick`函数返回连续时钟计时周期之间的秒。