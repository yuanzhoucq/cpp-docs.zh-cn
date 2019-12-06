---
title: _get_FMA3_enable、_set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: dee75bf5b16b5fe5b619444f7f2736010bb42a84
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857799"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable、_set_FMA3_enable

获取或设置一个标志，该标志指定超越数学浮点库函数是否使用为 X64 平台编译的代码中的 FMA3 指令。

## <a name="syntax"></a>语法

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>参数

*flag*<br/>
如果设置为1，则在 X64 平台上启用超越数学浮点库函数的 FMA3 实现; 如果为0，则使用不使用 FMA3 指令的实现。

## <a name="return-value"></a>返回值

如果启用了超越数学浮点库函数的 FMA3 实现，则为非零值。 否则为零。

## <a name="remarks"></a>备注

使用 **_set_FMA3_enable**函数可以启用或禁用在 CRT 库的超越数学浮点函数中使用 FMA3 指令。 返回值反映更改后使用的实现。 如果 CPU 不支持 FMA3 指令，则此函数将无法在库中启用它们，并且返回值为零。 使用 **_get_FMA3_enable**获取库的当前状态。 默认情况下，在 X64 平台上，CRT 启动代码检测 CPU 是否支持 FMA3 指令，并启用或禁用库中的 FMA3 实现。

由于 FMA3 实现使用不同的算法，因此当启用或禁用 FMA3 实现时，或在具有或不支持 FMA3 的计算机之间，可能会观察到计算结果的细微差异。 有关详细信息，请参阅[浮点迁移问题](../../porting/floating-point-migration-issues.md)。

## <a name="requirements"></a>需求

**_Set_FMA3_enable**和 **_get_FMA3_enable**函数仅适用于 X64 版本的 CRT。

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_FMA3_enable**， **_get_FMA3_enable**| C：\<math.h><br />C++： \<h > 或 \<math >|

**_Set_FMA3_enable**和 **_Get_FMA3_enable**函数是 Microsoft 特定的。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[浮点迁移问题](../../porting/floating-point-migration-issues.md)<br/>
