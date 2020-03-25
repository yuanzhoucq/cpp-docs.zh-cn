---
title: 链接器工具错误 LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194741"
---
# <a name="linker-tools-error-lnk2013"></a>链接器工具错误 LNK2013

修正类型修正溢出。 目标 "symbol name" 超出范围

由于目标符号与指令的位置相差太远，链接器无法将所需的地址或偏移量调整到给定指令中。

您可以通过创建多个映像或使用[/order](../../build/reference/order-put-functions-in-order.md)选项来解决此问题，以便说明和目标更接近。

如果符号名称是用户定义的符号（而不是编译器生成的符号），则还可以尝试以下操作来解决该错误：

- 将静态函数更改为非静态。

- 重命名包含静态函数的代码节，使其与调用方相同。

使用 `DUMPBIN /SYMBOLS`查看函数是否是静态的。
