---
title: 链接器工具警告 LNK4219 |Microsoft 文档
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
ms.openlocfilehash: 59cb7376957b7985b7ae2335ea472171d490ff42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301130"
---
# <a name="linker-tools-warning-lnk4219"></a>链接器工具警告 LNK4219
修正名称修正溢出。 目标目标 symbol name 不在范围内，插入转换 （thunk）  
  
 链接器的地址或偏移量不能适应中给定的指令，因为目标符号太远距离指令的位置的情况下插入一个 thunk。  
  
 你可能想要重新排序映像 (使用[/order](../../build/reference/order-put-functions-in-order.md)选项，例如) 以避免额外级别的间接寻址。