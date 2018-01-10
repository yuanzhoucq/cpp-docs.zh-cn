---
title: "链接器工具警告 LNK4219 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4219
dev_langs: C++
helpviewer_keywords: LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1331931ba2fa7219a27b8f60b185dc3ab9310328
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4219"></a>链接器工具警告 LNK4219
修正名称修正溢出。 目标目标 symbol name 不在范围内，插入转换 （thunk）  
  
 链接器的地址或偏移量不能适应中给定的指令，因为目标符号太远距离指令的位置的情况下插入一个 thunk。  
  
 你可能想要重新排序映像 (使用[/order](../../build/reference/order-put-functions-in-order.md)选项，例如) 以避免额外级别的间接寻址。