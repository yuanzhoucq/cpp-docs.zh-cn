---
title: "_close | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _close
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _close
dev_langs:
- C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 9dab323afc6c70e81592119e0cec2775c239d87f
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="close"></a>_close
关闭文件。  
  
## <a name="syntax"></a>语法  
  
```  
int _close(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fd`  
 引用打开的文件的文件说明符。  
  
## <a name="return-value"></a>返回值  
 如果已成功关闭该文件，则 `_close` 返回 0。 返回值-1 指示错误。  
  
## <a name="remarks"></a>备注  
 `_close` 函数将关闭与 `fd` 关联的文件。  
  
 文件描述符和基础 OS 文件句柄已关闭。 因此，如果使用 Win32 函数 `CreateFile` 最初打开此文件并使用 `_open_osfhandle` 转换为文件描述符，则无需调用 `CloseHandle`。  
  
 此函数验证其参数。 如果 `fd` 是无效的文件描述符，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，该函数将返回 -1 并将 `errno` 设置为 `EBADF`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_close`|\<io.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_open](../../c-runtime-library/reference/open-wopen.md) 示例。  
  
## <a name="see-also"></a>另请参阅  
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_unlink、_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)
