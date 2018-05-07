---
title: 链接器工具错误 LNK2017 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095423b5f2d86cef309ed4316ff72d195b11eb26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2017"></a>链接器工具错误 LNK2017
symbol 重定位到领域而无需 /LARGEADDRESSAWARE:NO 无效  
  
 正在尝试生成 32 位地址的 64 位映像。 若要执行此操作，你必须：  
  
-   使用固定的负载地址。  
  
-   将图像限制为 3 GB。  
  
-   指定[/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md)。