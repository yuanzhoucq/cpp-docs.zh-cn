---
title: 堆栈使用情况 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 827a129c0b7a444cc5b48ba68a3e360712e1c08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721534"
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