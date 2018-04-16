---
title: "链接器工具警告 LNK4037 |Microsoft 文档"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c93eab2faf81e4cd743eae4befa2f842c100589
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4037"></a>链接器工具警告 LNK4037

>*符号*不存在; 被忽略

修饰的名*符号*不能由使用排序[/order](../../build/reference/order-put-functions-in-order.md)选项，因为它找不到程序中。 检查的规范*符号*顺序响应文件中。 有关详细信息，请参阅[/ORDER （按顺序放置函数）](../../build/reference/order-put-functions-in-order.md)链接器选项。

> [!NOTE]
> 链接无法排序静态函数，因为静态函数名称不是公共符号名称。 当**/order**是指定，此链接器警告生成是静态的顺序响应文件中的每个符号，或者未找到。