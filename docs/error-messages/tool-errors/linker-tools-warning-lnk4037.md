---
title: 链接器工具警告 LNK4037 |Microsoft 文档
ms.custom: ''
ms.date: 10/04/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b87f0a415d6ae7d282e29c2ca67fda043c2a901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302430"
---
# <a name="linker-tools-warning-lnk4037"></a>链接器工具警告 LNK4037

>*符号*不存在; 被忽略

修饰的名*符号*不能由使用排序[/order](../../build/reference/order-put-functions-in-order.md)选项，因为它找不到程序中。 检查的规范*符号*顺序响应文件中。 有关详细信息，请参阅[/ORDER （按顺序放置函数）](../../build/reference/order-put-functions-in-order.md)链接器选项。

> [!NOTE]
> 链接无法排序静态函数，因为静态函数名称不是公共符号名称。 当 **/order**是指定，此链接器警告生成是静态的顺序响应文件中的每个符号，或者未找到。