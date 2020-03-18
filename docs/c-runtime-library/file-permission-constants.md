---
title: 文件权限常量
ms.date: 11/04/2016
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 9f6126b867e29ca37468c6ff383224a483639c78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443275"
---
# <a name="file-permission-constants"></a>文件权限常量

## <a name="syntax"></a>语法

```
#include <sys/stat.h>
```

## <a name="remarks"></a>备注

当指定 `_O_CREAT`（`_open` 或 `_sopen`）时需要这些常量中的一个。

`pmode` 参数按以下方式指定文件的权限设置。

|常量|含义|
|--------------|-------------|
|`_S_IREAD`|允许读取|
|`_S_IWRITE`|允许写入|
|`_S_IREAD` &#124; `_S_IWRITE`|允许读取和写入。|

当用作 `pmode` 的 `_umask` 参数时，清单常量将设置权限设置，如下所示。

|常量|含义|
|--------------|-------------|
|`_S_IREAD`|不允许写入（文件是只读的）|
|`_S_IWRITE`|不允许读取（文件是只写的）|
|`_S_IREAD` &#124; `_S_IWRITE`|既不允许读取也不允许写入|

## <a name="see-also"></a>另请参阅

[_open、_wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[标准类型](../c-runtime-library/standard-types.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
