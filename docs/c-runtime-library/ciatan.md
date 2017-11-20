---
title: "_CIatan |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIatan
apilocation:
- msvcr120.dll
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- _CIatan
- CIatan
dev_langs: C++
helpviewer_keywords:
- CIatan intrinsic
- _CIatan intrinsic
ms.assetid: 3baa0429-fe46-4bab-8b00-868e2186dc8c
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4c1fb3c3cdd3d83c7fff095ed9777a6c2fad8f83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ciatan"></a>_CIatan
计算堆栈顶部值的反正切值。  
  
## <a name="syntax"></a>语法  
  
```  
void __cdecl _CIatan();  
```  
  
## <a name="remarks"></a>备注  
 此版本的 `atan` 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。  
  
 生成的值被将被推送到堆栈顶部。  
  
## <a name="requirements"></a>要求  
 **平台：**x86  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)