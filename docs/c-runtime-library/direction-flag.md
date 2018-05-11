---
title: 方向标志 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3737304d2443b4f67f00a03e23a0529ad5bcbfe3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="direction-flag"></a>方向标志
方向标志是特定于 Intel 80x86 处理器的 CPU 标识。 它适用于所有使用 REP（重复）前缀的程序集指令，如 MOVS、MOVSD、MOVSW 等。 如果清除了方向标志，为适用的指令提供的地址将会增加。  
  
 C 运行期例程假定方向标志已清除。 如果要将其他函数与 C 运行时函数一起使用，您必须确保其他函数让方向标志保持不变或将其还原为原始状态。 在输入时期望方向标志保持清晰将使运行时代码更加快速高效。  
  
 C 运行库函数（如字符串操作和缓冲区操作例程）期望方向标志保持清晰。  
  
## <a name="see-also"></a>请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)