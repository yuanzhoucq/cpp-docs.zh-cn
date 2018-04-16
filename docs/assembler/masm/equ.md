---
title: EQU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- EQU
dev_langs:
- C++
helpviewer_keywords:
- EQU directive
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 545fa7bcc7b853fd787ee085a6d656fd184797fb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
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