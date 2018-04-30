---
title: POPCONTEXT |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- POPCONTEXT
dev_langs:
- C++
helpviewer_keywords:
- POPCONTEXT directive
ms.assetid: 19f59290-a54d-477d-88d8-97d3f63ed417
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bb33ef4415dc6c60f675aa72c6fea9deb69c287
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="popcontext"></a>POPCONTEXT
还原部分或全部当前`context`(由保存[PUSHCONTEXT](../../assembler/masm/pushcontext.md)指令)。 `context`可以是**假设**， `RADIX`，**列出**， **CPU**，或**所有**。  
  
## <a name="syntax"></a>语法  
  
```  
  
POPCONTEXT context  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)