---
title: "_commit | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _commit
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
- _commit
- commit
dev_langs:
- C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: 14
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
ms.openlocfilehash: 40d0fdf7d64dca941c952921d1c3107baa910a74
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="commit"></a>_commit
将文件直接刷新到磁盘。  
  
## <a name="syntax"></a>语法  
  
```  
int _commit(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fd`  
 引用打开的文件的文件说明符。  
  
## <a name="return-value"></a>返回值  
 如果文件已成功刷新到磁盘，则 `_commit` 返回 0。 返回值-1 指示错误。  
  
## <a name="remarks"></a>备注  
 `_commit` 函数强制操作系统将与 `fd` 关联的文件写入到磁盘。 此调用可确保立即刷新特定文件，而无需等待操作系统的决定。  
  
 如果 `fd` 是无效的文件描述符，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数将返回 -1 并将 `errno` 设置为 `EBADF`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|----------------------|  
|`_commit`|\<io.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_read](../../c-runtime-library/reference/read.md)   
 [_write](../../c-runtime-library/reference/write.md)
