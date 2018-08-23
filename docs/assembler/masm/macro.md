---
title: 宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MACRO
dev_langs:
- C++
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2b7469314bc1b65f960df1ca582acb6dbb4624e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054440"
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