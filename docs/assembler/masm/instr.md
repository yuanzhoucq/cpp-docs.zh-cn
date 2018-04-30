---
title: INSTR |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- InStr
dev_langs:
- C++
helpviewer_keywords:
- INSTR directive
ms.assetid: fc37f6a2-3c95-47b2-b6bb-1066edd25994
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dd640aafe78f99f50d98569792d0c1c5ef330ee
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="instr"></a>INSTR
查找的第一个匹配项*textitem2*中*textitem1*。  
  
## <a name="syntax"></a>语法  
  
```  
  
name  
 INSTR [[position,]] textitem1, textitem2  
```  
  
## <a name="remarks"></a>备注  
 起始*位置*是可选的。 每个文本项可以是文本字符串，前面是一个常数`%`，或通过宏函数返回的字符串。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)