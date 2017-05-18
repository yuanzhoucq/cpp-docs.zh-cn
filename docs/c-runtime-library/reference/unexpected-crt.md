---
title: "unexpected (CRT) | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- unexpected
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
apitype: DLLExport
f1_keywords:
- unexpected
dev_langs:
- C++
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
caps.latest.revision: 10
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
ms.openlocfilehash: 7e1188d3cf2136e67d2e212640b2c2c29b7cf1f5
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="unexpected-crt"></a>unexpected (CRT)
调用 `terminate` 或使用 `set_unexpected` 指定的函数。  
  
## <a name="syntax"></a>语法  
  
```  
void unexpected( void );  
```  
  
## <a name="remarks"></a>备注  
 `unexpected` 例程不与 C++ 异常处理的当前实现一起使用。 默认情况下，`unexpected` 调用 `terminate`。 您可以通过以下方式更改此默认行为：编写自定义终止函数并调用 `set_unexpected`（将该函数的名称作为其参数）。 `unexpected` 调用作为 `set_unexpected` 的参数提供的最后一个函数。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`unexpected`|\<eh.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另请参阅  
 [异常处理例程](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)   
 [set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)
