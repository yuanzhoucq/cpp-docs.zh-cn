---
title: 函数类型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dfb36dc9e177fdb9ad196c0e2a8ad0f352d5f2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709561"
---
# <a name="function-types"></a>函数类型

基本上，有两种类型的函数。 需要一个堆栈帧的函数称为帧函数。 不需要的堆栈帧的函数被称为叶函数。

帧函数是分配堆栈空间、 调用其他函数中，将非易失寄存器保存或使用异常处理的函数。 它还需要函数表条目。 帧函数需要一个 prolog 和 epilog。 帧函数可以动态地分配堆栈空间，并可以使用帧指针。 框架函数具有的全部功能调用其可供使用的标准。

如果帧函数不会调用另一个函数，则不需要对齐堆栈 (部分中提到[堆栈分配](../build/stack-allocation.md))。

叶函数是一个不需要函数表条目。 它不能为任何非易失性寄存器，包括 RSP，这意味着它不能调用任何函数或分配堆栈空间进行更改。 它允许它执行的同时保留堆栈未对齐。

## <a name="see-also"></a>请参阅

[堆栈使用](../build/stack-usage.md)
