---
title: "从 NMAKE 退出代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13cbe4806d8b3960cbf80df41c7cce6e7657ba7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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