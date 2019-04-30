---
title: 链接器工具警告 LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410247"
---
# <a name="linker-tools-warning-lnk4219"></a>链接器工具警告 LNK4219

链接地址信息名称的链接地址信息溢出。 目标目标 symbol name 不在范围内，正在插入 thunk

链接器的地址或偏移量不能使在给定的指令中，因为目标符号太远而从指令的位置的情况下插入一个 thunk。

你可能想要对图像进行重新排序 (使用[/O](../../build/reference/order-put-functions-in-order.md)选项，例如) 以避免额外级别的间接寻址。