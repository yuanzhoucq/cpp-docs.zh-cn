---
title: 从 NMAKE 退出代码 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e71442e1e36dbd69afa65051cbf08f403bf8b31
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367090"
---
# <a name="exit-codes-from-nmake"></a>从 NMAKE 退出代码
NMAKE 返回下列退出代码：  
  
|代码|含义|  
|----------|-------------|  
|0|无错误 （可能是警告）|  
|1|不完整的生成 （仅在使用 /K 时发出）|  
|2|程序错误，可能是因为下列情况之一：|  
||的在生成文件中语法错误|  
||的来自命令错误或退出代码|  
||-用户中断|  
|4|系统错误-内存不足|  
|255|目标不是最新的 （仅在使用 /Q 时发出）|  
  
## <a name="see-also"></a>请参阅  
 [运行 NMAKE](../build/running-nmake.md)