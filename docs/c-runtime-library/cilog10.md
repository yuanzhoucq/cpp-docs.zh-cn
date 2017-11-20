---
title: "_CIlog10 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIlog10
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIlog10
- _CIlog10
dev_langs: C++
helpviewer_keywords:
- _CIlog10 intrinsic
- CIlog10 intrinsic
ms.assetid: 05d7fcaa-3cff-4cc5-8d44-015e7cacba24
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8eb203750491475b7e615d5f7d3ff940a772f6a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cilog10"></a>_CIlog10
对堆栈顶部的值执行 `log10` 运算。  
  
## <a name="syntax"></a>语法  
  
```  
void __cdecl _CIlog10();  
```  
  
## <a name="remarks"></a>备注  
 此版本的 `log10` 函数具有编译器理解的专用化调用约定。 该函数将加快执行的速度，因为它可防止生成副本和帮助注册表分配。  
  
 生成的值被将被推送到堆栈顶部。  
  
## <a name="requirements"></a>要求  
 **平台：**x86  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)