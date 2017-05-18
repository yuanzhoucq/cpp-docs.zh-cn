---
title: "srand | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- srand
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: e86ea8aa561af584a6825d4225820aca7baeced2
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="srand"></a>srand
设置为伪随机数生成器的起始种子值。  
  
## <a name="syntax"></a>语法  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### <a name="parameters"></a>参数  
 `seed`  
 伪随机数生成的种子  
  
## <a name="remarks"></a>备注  
 `srand` 函数在当前线程中设置生成一系列伪随机整数的起点。 若要重新初始化生成器以创建相同的结果序列，请调用 `srand` 函数并再次使用相同的 `seed` 参数。 `seed` 的任何其他值将生成器设置为伪随机序列中的不同起始点。 `rand` 检索生成的伪随机数。 在任何调用 `srand` 之前调用 `rand` 可生成与调用 `srand` 相同的序列，`seed` 作为 1 传递。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`srand`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [rand](../../c-runtime-library/reference/rand.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [rand](../../c-runtime-library/reference/rand.md)
