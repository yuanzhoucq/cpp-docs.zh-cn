---
title: _findclose
ms.date: 11/04/2016
api_name:
- _findclose
api_location:
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: c67336cc12bcdee754edd40b91078faa83a17984
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957323"
---
# <a name="_findclose"></a>_findclose

关闭指定的搜索句柄并释放关联资源。

## <a name="syntax"></a>语法

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>参数

*柄*<br/>
之前对 **_findfirst**的调用返回的搜索句柄。

## <a name="return-value"></a>返回值

如果成功， **_findclose**将返回0。 否则，它将返回-1，并将**errno**设置为**ENOENT**，指示找不到更多匹配的文件。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_findclose**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[系统调用](../../c-runtime-library/system-calls.md)<br/>
[文件名搜索函数](../../c-runtime-library/filename-search-functions.md)<br/>
