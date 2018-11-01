---
title: 3.3 计时例程
ms.date: 11/04/2016
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
ms.openlocfilehash: 404e9e168c916b70c7cd32042822f290cd560e98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630469"
---
# <a name="33-timing-routines"></a>3.3 计时例程

在本部分中所述的函数支持可移植的时钟计时器：

- `omp_get_wtime`函数将返回已用的时钟时间。

- `omp_get_wtick`函数返回连续的时钟计时周期之间的秒。