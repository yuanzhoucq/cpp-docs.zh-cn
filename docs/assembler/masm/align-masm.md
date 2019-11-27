---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 22b18f2e238c780377b84fc2be3eb6678686bb73
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399275"
---
# <a name="align-masm"></a>ALIGN (MASM)

**ALIGN**指令将下一个数据元素或指令与作为其参数的倍数的地址对齐。 参数必须是2的幂（例如，1、2、4等等），小于或等于段对齐。

## <a name="syntax"></a>语法

> **ALIGN** ⟦*number*⟧

## <a name="remarks"></a>备注

**ALIGN**指令允许您指定数据元素或指令的开始偏移量。 对齐的数据可以提高性能，但代价是数据元素之间浪费的空间。 当数据访问位于缓存行内的边界时，可以查看较大的性能改进。 本机类型的自然边界访问意味着在内部硬件调整微码中花费的时间更少。

在使用平面寻址模型的新式处理器上，很少需要对齐说明，但对于其他寻址模型，较旧代码中的跳转目标可能需要这些说明。

当数据对齐时，跳过的空间用零填充。 对齐指令时，将用适当大小的 NOP 指令填充跳过的空间。

## <a name="see-also"></a>另请参阅

[即使](even.md)\
[指令参考](directives-reference.md)
