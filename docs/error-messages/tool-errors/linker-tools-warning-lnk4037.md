---
title: 链接器工具警告 LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607397"
---
# <a name="linker-tools-warning-lnk4037"></a>链接器工具警告 LNK4037

>'*符号*不存在; 已忽略

修饰的名*符号*不可能通过使用按序[/O](../../build/reference/order-put-functions-in-order.md)选项，因为它找不到程序中。 检查的规范*符号*订单响应文件中。 有关详细信息，请参阅[/ORDER （按顺序放置函数）](../../build/reference/order-put-functions-in-order.md)链接器选项。

> [!NOTE]
> 链接不能进行排序的静态函数，因为静态函数名称不是公共符号名称。 当 **/O**指定，此链接器警告生成的是静态的订单响应文件中每个符号或找不到。