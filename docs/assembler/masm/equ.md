---
title: 等于 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EQU
dev_langs:
- C++
helpviewer_keywords:
- EQU directive
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d7678cac4c480934fe9f6dd9816e636481c2d64
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050745"
---
# <a name="equ"></a>EQU
第一个指令将分配数字值*表达式*到*名称*。  
  
## <a name="syntax"></a>语法  
  
```  
  
      name EQU expression  
name EQU <text>  
```  
  
## <a name="remarks"></a>备注  
 *名称*不能重新定义更高版本。  
  
 指定第二个指令分配*文本*到*名称*。 *名称*可以分配不同*文本*更高版本。 请参阅[TEXTEQU](../../assembler/masm/textequ.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)