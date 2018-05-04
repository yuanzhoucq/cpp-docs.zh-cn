---
title: fwide | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fwide
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
- fwide
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd52c450e2eb34c40d44d00a76550c401abcb6c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fwide"></a>fwide

未实现。

## <a name="syntax"></a>语法

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构 （忽略）。

*模式*<br/>
流的新宽度：宽字符为正，字节为负，保持不变的为零。 （将忽略此值。）

## <a name="return-value"></a>返回值

此函数当前仅返回*模式*。

## <a name="remarks"></a>备注

此函数的当前版本不符合标准。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。