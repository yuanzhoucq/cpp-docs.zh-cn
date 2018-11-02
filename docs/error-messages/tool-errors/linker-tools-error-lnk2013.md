---
title: 链接器工具错误 LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 4d932a89f1b0bde27f6de2f84b2ed103dab1b1b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620722"
---
# <a name="linker-tools-error-lnk2013"></a>链接器工具错误 LNK2013

链接地址信息类型的链接地址信息溢出。 目标 symbol name 不在范围内

链接器不能使必需的地址或偏移量为给定的指令，因为目标符号太远距离指令的位置。

您可以通过创建多个映像，或解决此问题[/O](../../build/reference/order-put-functions-in-order.md)选项使指令和目标靠近。

用户定义的符号 （而不是编译器生成的符号） 的符号名称时，您还可以尝试以下操作来解决此错误：

- 更改为非静态的静态函数。

- 重命名包含静态函数以调用方相同的代码段。

使用`DUMPBIN /SYMBOLS`，以查看函数是静态。