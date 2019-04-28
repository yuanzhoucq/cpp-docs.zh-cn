---
title: feupdateenv
ms.date: 04/05/2018
apiname:
- feupdateenv
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
apitype: HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 6d553d6899f55f5bdfb3ff313e88abfcb56ab4ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334069"
---
# <a name="feupdateenv"></a>feupdateenv

保存当前引发的浮点异常，还原指定的浮点环境状态，并引发已保存的浮点异常。

## <a name="syntax"></a>语法

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>参数

*penv*<br/>
指向**fenv_t**对象，其中包含作为组的浮点环境，通过调用[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)。 此外，也可以通过使用 FE_DFL_ENV 宏指定默认启动浮点环境。

## <a name="return-value"></a>返回值

如果所有操作已成功完成，则返回 0。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Feupdateenv**函数执行多个操作。 首先，它在自动存储中存储当前引发的浮点异常状态标志。 然后，它设置当前浮点环境中存储的值从**fenv_t**指向对象*penv*。 如果*penv*不是**FE_DFL_ENV**或不指向有效**fenv_t**对象，则未定义后续行为。 最后， **feupdateenv**引发本地存储的浮点异常。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
