---
title: 链接器工具警告 LNK4219 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daf097cd8715a7c523e6e8a2ea46714481ca7d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105197"
---
# <a name="linker-tools-warning-lnk4219"></a>链接器工具警告 LNK4219

链接地址信息名称的链接地址信息溢出。 目标目标 symbol name 不在范围内，正在插入 thunk

链接器的地址或偏移量不能使在给定的指令中，因为目标符号太远而从指令的位置的情况下插入一个 thunk。

你可能想要对图像进行重新排序 (使用[/O](../../build/reference/order-put-functions-in-order.md)选项，例如) 以避免额外级别的间接寻址。