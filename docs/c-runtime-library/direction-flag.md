---
title: 方向标志
ms.date: 11/04/2016
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: 04e096c6a62f806f4c214745a8401b1730eda3a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443378"
---
# <a name="direction-flag"></a>方向标志

方向标志是特定于所有兼容 Intel x86 CPU 的 CPU 标志。 它适用于所有使用 REP（重复）前缀的程序集指令，如 MOVS、MOVSD、MOVSW 等。 如果清除了方向标志，为适用的指令提供的地址将会增加。

C 运行期例程假定方向标志已清除。 如果要将其他函数与 C 运行时函数一起使用，您必须确保其他函数让方向标志保持不变或将其还原为原始状态。 在输入时期望方向标志保持清晰将使运行时代码更加快速高效。

C 运行库函数（如字符串操作和缓冲区操作例程）期望方向标志保持清晰。

## <a name="see-also"></a>另请参阅

[CRT 库功能](../c-runtime-library/crt-library-features.md)
