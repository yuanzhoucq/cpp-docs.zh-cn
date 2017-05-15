---
title: "_CrtMemDumpAllObjectsSince | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 93904e03c38a74005682aabfc30c69b6f96b14c7
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince
从程序开始执行或从指定的堆状态转储堆中对象的信息（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>参数  
 `state`  
 指向开始从其转储的堆状态的指针，或 **NULL**。  
  
## <a name="remarks"></a>备注  
 `_CrtMemDumpAllObjectsSince` 函数以用户可读的形式转储堆中分配的对象的调试标头信息。 应用程序可以使用转储信息来跟踪分配并检测内存问题。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtMemDumpAllObjectsSince` 的调用。  
  
 `_CrtMemDumpAllObjectsSince` 使用 `state` 参数的值确定启动转储操作的位置。 要从指定堆状态开始转储，`state` 参数必须是指向 **_CrtMemState** 结构的指针，此结构在调用 `_CrtMemDumpAllObjectsSince` 前已由 [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填充。 当 `state` 为 **NULL** 时，该函数从程序开始执行时即开始转储。  
  
 如果应用程序通过调用 [_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md) 安装了转储挂钩函数，那么每次 `_CrtMemDumpAllObjectsSince` 转储有关 `_CLIENT_BLOCK` 块类型的信息时，它都会调用应用程序提供的转储函数。 默认情况下，内存转储操作不包含内部 C 运行时块 (`_CRT_BLOCK`)。 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可用于打开 **_crtDbgFlag** 的 `_CRTDBG_CHECK_CRT_DF` 位，以将这些块包括在内。 此外，标记为已释放或已忽略的块（**_FREE_BLOCK**、**_IGNORE_BLOCK**）不包括在内存转储中。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="example"></a>示例  
 有关如何使用 `_CrtMemDumpAllObjectsSince` 的示例，请参阅 [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)
