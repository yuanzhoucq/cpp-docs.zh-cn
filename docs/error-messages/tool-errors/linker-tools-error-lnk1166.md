---
title: "链接器工具错误 LNK1166 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1166
dev_langs:
- C++
helpviewer_keywords:
- LNK1166
ms.assetid: d69548a8-0efb-44e1-90b7-b27636a4b575
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d23c05fa543825f9bf5fbb2c7dc08f4b9473098
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1166"></a>链接器工具错误 LNK1166
无法调整代码偏移量 = 偏移量，va = 值  
  
 链接无法填充所需的代码。  
  
 某些指令不允许在某些处理器上跨页边界。 链接尝试将添加填充代码来纠正这种情况。 在这种情况下，链接可能不解决此问题。