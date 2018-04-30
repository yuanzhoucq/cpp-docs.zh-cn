---
title: 包括 (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- include
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE directive
ms.assetid: 1c7964ee-715c-414e-a45e-74af93476eb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 346f076e63df7b02928b5abf49def827229bb289
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="include-masm"></a>INCLUDE (MASM)
从给定的源文件插入源代码*filename*到程序集在当前的源文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
INCLUDE filename  
```  
  
## <a name="remarks"></a>备注  
 *Filename*必须括在尖括号中，如果它包含一个反斜杠，分号，更高的比符号，较少-比符号、 一个单引号或双引号。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)