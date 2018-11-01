---
title: 堆栈使用
ms.date: 11/04/2016
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 5ee9da50a03e1137ed6543cd349481148c9127d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452216"
---
# <a name="stack-usage"></a>堆栈使用

超出 RSP 的当前地址的所有内存均都视为易失性： 操作系统或调试程序，可能会在用户调试会话或中断处理程序过程覆盖此内存。 因此，RSP 必须始终设置然后再尝试读取或写入到堆栈帧的值。

本部分讨论的本地变量的堆栈空间分配和**alloca**内部函数。

- [堆栈分配](../build/stack-allocation.md)

- [构造动态的参数堆栈区域](../build/dynamic-parameter-stack-area-construction.md)

- [函数类型](../build/function-types.md)

- [malloc 对齐](../build/malloc-alignment.md)

- [alloca](../build/alloca.md)

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)