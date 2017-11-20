---
title: "__dllonexit |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords: __dllonexit
dev_langs: C++
helpviewer_keywords: __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9e59acec12c90d101ef385c379c092c7034f1ed0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="dllonexit"></a>__dllonexit
注册在退出时要调用的例程。  
  
## <a name="syntax"></a>语法  
  
```  
_onexit_t __dllonexit(   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### <a name="parameters"></a>参数  
 `func`  
 指向在退出时要执行的函数的指针。  
  
 `pbegin`  
 指向一个变量的指针，该变量指向要执行拆离的函数列表开端。  
  
 `pend`  
 指向一个变量的指针，该变量指向要执行拆离的函数列表末尾。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为指向用户函数的指针。 否则，为 NULL 指针。  
  
## <a name="remarks"></a>备注  
 该 `__dllonexit` 函数类似于 [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) 函数，只不过在此例程中看不到该函数使用的全局变量。 此函数使用 `pbegin` 和 `pend` 参数而不是全局变量。  
  
 DLL 中与 MSVCRT.LIB 链接的 `_onexit` 和 `atexit` 函数必须保留自己的 atexit/_onexit 列表。 此例程是由此类 DLL 调用的工作线程。  
  
 `_PVFV` 类型定义为 `typedef void (__cdecl *_PVFV)(void)`。  
  
## <a name="requirements"></a>要求  
  
|例程|所需文件|  
|-------------|-------------------|  
|__dllonexit|onexit.c|  
  
## <a name="see-also"></a>另请参阅  
 [_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)