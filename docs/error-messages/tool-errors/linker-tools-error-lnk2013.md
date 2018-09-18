---
title: 链接器工具错误 LNK2013 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04ce4ca8079317da090cf05d43f41e4e40a6b19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041735"
---
# <a name="linker-tools-error-lnk2013"></a>链接器工具错误 LNK2013

链接地址信息类型的链接地址信息溢出。 目标 symbol name 不在范围内

链接器不能使必需的地址或偏移量为给定的指令，因为目标符号太远距离指令的位置。

您可以通过创建多个映像，或解决此问题[/O](../../build/reference/order-put-functions-in-order.md)选项使指令和目标靠近。

用户定义的符号 （而不是编译器生成的符号） 的符号名称时，您还可以尝试以下操作来解决此错误：

- 更改为非静态的静态函数。

- 重命名包含静态函数以调用方相同的代码段。

使用`DUMPBIN /SYMBOLS`，以查看函数是静态。