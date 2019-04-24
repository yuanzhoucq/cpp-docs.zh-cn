---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166472"
---
# <a name="align-masm"></a>ALIGN (MASM)

**对齐**指令对齐的下一个数据元素或其参数的倍数的地址上的指令。 参数必须是 2 的幂 （例如，1、 2、 4 和等等），它是小于或等于为段对齐方式。

## <a name="syntax"></a>语法

> 对齐 [[*数*]]

## <a name="remarks"></a>备注

**对齐**指令允许您指定的数据元素或指令的开始偏移量。 对齐的数据可以提高性能，代价是数据元素之间的浪费空间。 当数据访问是适合缓存行的边界上，可以查看较大性能改进。 本机类型的自然边界访问意味着所花费的内部硬件重新调整了微代码更少时间。

有关对齐的说明的要求是在现代处理器中，使用平面的寻址模式，但在较旧代码中的其他寻址模型可能要求的跳转目标少见。

如果数据为 aligned，已跳过的空间是用零填充。 一致的说明，已跳过的空间是由相应地调整大小 NOP 指令的填充。

## <a name="see-also"></a>请参阅

[EVEN](even.md)<br/>
[指令参考](../../assembler/masm/directives-reference.md)<br/>