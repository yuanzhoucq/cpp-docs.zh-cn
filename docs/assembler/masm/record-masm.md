---
title: 记录 (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- RECORD
dev_langs:
- C++
helpviewer_keywords:
- RECORD directive
ms.assetid: c83db394-0fe3-468f-813f-13302cdc862d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e726053a9146cf88ed4e84045118d19b7094ed37
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057256"
---
# <a name="record-masm"></a>RECORD (MASM)
声明一包含的指定字段的记录类型。 *fieldname*名称字段，*宽度*指定的位数，和*表达式*提供其初始值。  
  
## <a name="syntax"></a>语法  
  
```  
  
   recordname RECORD fieldname:width [[= expression]]   
[[, fieldname:width [[= expression]]]]...  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)