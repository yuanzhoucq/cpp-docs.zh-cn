---
title: 链接器工具警告 LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 4488539a4f7282180048f1e3530e62e35c3b339e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183093"
---
# <a name="linker-tools-warning-lnk4219"></a>链接器工具警告 LNK4219

修正名称修正溢出。 目标 "目标符号名称" 超出范围，正在插入 thunk

由于目标符号与指令的位置距离太远，因此，链接器在地址或偏移量无法满足给定指令的情况下插入了 thunk。

您可能想要对图像重新排序（例如，使用[/order](../../build/reference/order-put-functions-in-order.md)选项），以避免额外的间接级别。
