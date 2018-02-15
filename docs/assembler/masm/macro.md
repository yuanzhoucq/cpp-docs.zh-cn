---
title: MACRO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MACRO
dev_langs:
- C++
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43289b487ad4076aa8208c4f9ecf2e24c67b2373
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="macro"></a>MACRO
标记调用一个宏块*名称*并建立*参数*时宏调用传递自变量的占位符。  
  
## <a name="syntax"></a>语法  
  
```  
  
   name MACRO [[parameter [[:REQ | :=default | :VARARG]]]]...  
statements  
ENDM [[value]]  
```  
  
## <a name="remarks"></a>备注  
 宏函数返回*值*于调用语句。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)