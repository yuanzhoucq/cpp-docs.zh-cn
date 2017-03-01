---
title: "_CrtSetDumpClient | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 035851454e2f163ea013a7240d6699db402565d3
ms.lasthandoff: 02/24/2017

---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient
安装应用程序定义的函数以转储 `_CLIENT_BLOCK` 类型的内存块（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### <a name="parameters"></a>参数  
 `dumpClient`  
 将新的客户端定义的内存转储函数挂钩到 C 运行时调试内存转储进程。  
  
## <a name="return-value"></a>返回值  
 返回之前定义的客户端块转储函数。  
  
## <a name="remarks"></a>备注  
 `_CrtSetDumpClient` 函数允许应用程序挂起自己的函数，以将存储在 `_CLIENT_BLOCK` 内存块中的对象转储到 C 运行时调试内存转储进程中。 因此，每次调试转储函数（如 [_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 或 [_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md)）转储 `_CLIENT_BLOCK` 内存块时，同时也会调用应用程序的转储函数。 `_CrtSetDumpClient` 为应用程序提供了一种检测内存泄漏以及验证或报告存储在 `_CLIENT_BLOCK` 块中的数据内容的简单方法。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtSetDumpClient` 的调用。  
  
 `_CrtSetDumpClient` 函数安装在 `dumpClient` 中指定的新的应用程序定义的转储函数，并返回之前定义的转储函数。 客户端块转储函数示例如下：  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 `userPortion` 参数是指向内存块的用户数据部分开始处的指针，`blockSize` 指定所分配的内存块的大小（以字节为单位）。 客户端块转储函数必须返回 `void`。 指向传递给 `_CrtSetDumpClient` 的客户端转储函数的指针是 `_CRT_DUMP_CLIENT` 类型，如 Crtdbg.h 中所定义：  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 有关在 `_CLIENT_BLOCK` 类型内存块上操作的函数的详细信息，请参阅[客户端块挂钩函数](/visualstudio/debugger/client-block-hook-functions)。 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md) 函数可用于返回有关块类型和子类型的信息。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtSetDumpClient`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)
