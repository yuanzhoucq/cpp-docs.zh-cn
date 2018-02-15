---
title: "_get_fmode | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_fmode
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
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: abfdd4d9b8838914a91b4db995fcaad573e80829
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="getfmode"></a>_get_fmode
获取文件 I/O 操作的默认文件转换模式。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pmode`  
 一个指向要用当前默认模式填充的整数的指针：`_O_TEXT` 或 `_O_BINARY`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回零；如果失败，则返回错误代码。 如果 `pmode` 为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 函数获取 [_fmode](../../c-runtime-library/fmode.md) 全局变量的值。 此变量为底层和流文件 I/O 操作指定默认文件转换模式，如 `_open`、`_pipe`、`fopen` 和 `freopen`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_get_fmode`|\<stdlib.h>|\<fcntl.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [_set_fmode](../../c-runtime-library/reference/set-fmode.md) 中的示例。  
  
## <a name="see-also"></a>请参阅  
 [_fmode](../../c-runtime-library/fmode.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)