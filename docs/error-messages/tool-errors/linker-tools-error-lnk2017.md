---
title: "链接器工具错误 LNK2017 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2017
dev_langs: C++
helpviewer_keywords: LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9446cb72ba9380e57b014b32d9ae00f6e9e554d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2017"></a>链接器工具错误 LNK2017
symbol 重定位到领域而无需 /LARGEADDRESSAWARE:NO 无效  
  
 正在尝试生成 32 位地址的 64 位映像。 若要执行此操作，你必须：  
  
-   使用固定的负载地址。  
  
-   将图像限制为 3 GB。  
  
-   指定[/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md)。