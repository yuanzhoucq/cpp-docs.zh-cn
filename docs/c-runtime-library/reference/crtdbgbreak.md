---
title: "_CrtDbgBreak | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
dev_langs:
- C++
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 105b86a3c06c17bd9d24ff6cedb213abf06dadcd
ms.lasthandoff: 02/24/2017

---
# <a name="crtdbgbreak"></a>_CrtDbgBreak
在特定代码行上设置断点。 （仅限调试模式。）  
  
## <a name="syntax"></a>语法  
  
```  
void _CrtDbgBreak( void );  
```  
  
## <a name="return-value"></a>返回值  
 没有返回值。  
  
## <a name="remarks"></a>备注  
 `_CrtDbgBreak` 函数在函数所在的特定代码上设置试断点。 此函数仅在调试模式下使用，并且依赖于之前的定义的 `_DEBUG`。  
  
 有关使用其他具有挂钩功能的运行时函数和编写你自己的客户端定义挂钩函数的详细信息，请参阅[编写你自己的调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtDbgBreak`|\<CRTDBG.h>|  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [__debugbreak](../../intrinsics/debugbreak.md)
