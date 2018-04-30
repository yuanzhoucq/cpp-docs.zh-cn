---
title: 页 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PAGE
dev_langs:
- C++
helpviewer_keywords:
- Page directive
ms.assetid: 6654c094-c1f7-4d10-8d9d-902ddd1ac27e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 994a542b543fd58fa970c373243f18403b167c1d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="page"></a>PAGE
第一个指令将设置行*长度*和字符*宽度*的程序列表。 如果未提供参数，将生成一个分页符。 第二个指令形式递增的节号，并将页码重置为 1。  
  
## <a name="syntax"></a>语法  
  
```  
  
      PAGE [[[[length]], width]]  
PAGE +  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)