---
title: "_setmbcp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
dev_langs:
- C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 42d2d43726ea533ab689a61c5211317c8dc033c4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="setmbcp"></a>_setmbcp
设置新的多字节代码页。  
  
## <a name="syntax"></a>语法  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### <a name="parameters"></a>参数  
 `codepage`  
 独立于区域设置的多字节例程的新代码页设置。  
  
## <a name="return-value"></a>返回值  
 如果已成功设置代码页，则返回 0。 如果为提供无效的代码页值`codepage`，返回-1 和代码页设置保持不变。 如果无法分配内存，则将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_setmbcp` 函数指定新的多字节代码页。 默认情况下，运行时系统将多字节代码页自动设置为系统默认的 ANSI 代码页。 多字节代码页设置将影响所有独立于区域设置的多字节例程。 但是，可能会指示 `_setmbcp` 使用为当前区域设置定义的代码页（请参阅以下清单常量和关联的行为结果的列表）。 有关依赖于区域设置代码页，而不是多字节代码页的多字节例程的列表，请参阅[多字节字符序列解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。  
  
 多字节代码页还会通过以下运行时库例程来影响多字节字符处理：  
  
||||  
|-|-|-|  
|[_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)|[_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)|[_splitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 此外，接收多字节字符 `argv` 或 `envp` 程序自变量作为参数（如 `_exec` 和 `_spawn` 系列）的所有运行时库例程会根据多字节代码页来处理这些字符串。 因此，这些例程还会受到对更改多字节代码页的 `_setmbcp` 的调用的影响。  
  
 可以将 `codepage` 自变量设置为以下值之一：  
  
-   `_MB_CP_ANSI` 使用在程序启动时从操作系统获取的 ANSI 代码页。  
  
-   `_MB_CP_LOCALE` 使用从以前对 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 的调用获取的当前区域设置的代码页。  
  
-   `_MB_CP_OEM` 使用在程序启动时从操作系统获取的 OEM 代码页。  
  
-   `_MB_CP_SBCS` 使用单字节代码页。 在将代码页设置为 `_MB_CP_SBCS` 时，如 [_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) 的例程始终返回 false。  
  
-   任何其他有效的代码页值，而不考虑该值是否为 ANSI、OEM 或其他操作系统支持的代码页（除不受支持的 UTF-7 和 UTF-8 以外）。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_setmbcp`|\<mbctype.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)