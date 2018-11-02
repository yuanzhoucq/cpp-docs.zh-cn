---
title: 与 x86 编译器冲突
ms.date: 11/04/2016
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
ms.openlocfilehash: e56ebc5631ac5c96a9cdd2dfc2b8e81cdeed9769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614261"
---
# <a name="conflicts-with-the-x86-compiler"></a>与 x86 编译器冲突

数据类型包含大于 4 个字节都不会自动对齐在堆栈上时使用 x86 编译器来编译应用程序。 因为编译器是 4 字节对齐的堆栈，任何大于 4 个字节，例如，64 位整数，不能自动对齐到 8 字节地址 x86 体系结构。

处理未对齐的数据有两个含义。

- 可能需要更长时间才能访问未对齐的位置不是所需访问对齐的位置。

- 未对齐的位置不能使用互锁操作中。

如果需要更为严格的对齐，请使用`__declspec(align(N)) on your variable declarations`。 这将导致编译器动态对齐的堆栈，以满足您的规范。 但是，在运行时动态调整堆栈可能会导致应用程序的执行速度变慢。

## <a name="see-also"></a>请参阅

[类型和存储](../build/types-and-storage.md)<br/>
[align](../cpp/align-cpp.md)