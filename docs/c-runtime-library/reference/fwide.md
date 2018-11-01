---
title: fwide
ms.date: 11/04/2016
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
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: d992ebc527744beeb4ef14175e3f10646a77a064
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557841"
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
指向**文件**结构 （已忽略）。

*模式*<br/>
流的新宽度：宽字符为正，字节为负，保持不变的为零。 （将忽略此值。）

## <a name="return-value"></a>返回值

此函数目前只返回*模式下*。

## <a name="remarks"></a>备注

此函数的当前版本不符合标准。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。