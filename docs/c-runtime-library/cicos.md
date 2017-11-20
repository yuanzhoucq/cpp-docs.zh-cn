---
title: "_CIcos |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
dev_langs: C++
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cab375ac2224ff4c3dfc8f66f84b69a5256f388f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cicos"></a>_CIcos
计算堆栈顶部值的余弦值。  
  
## <a name="syntax"></a>语法  
  
```  
void __cdecl _CIcos();  
```  
  
## <a name="remarks"></a>备注  
 此版本的 `cos` 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。  
  
 生成的值被将被推送到堆栈顶部。  
  
## <a name="requirements"></a>要求  
 **平台：**x86  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)