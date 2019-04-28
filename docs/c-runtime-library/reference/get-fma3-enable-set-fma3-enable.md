---
title: _get_fma3_enable、_set_fma3_enable
ms.date: 04/05/2018
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 19eabc3b5a11246d5b0056bdafbb169e2a7de9f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332190"
---
# <a name="getfma3enable-setfma3enable"></a>_get_fma3_enable、_set_fma3_enable

获取或设置一个标志，指定是否超越数学浮点库函数针对 X64 编译的代码中使用 FMA3 指令的平台。

## <a name="syntax"></a>语法

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>参数

*flag*<br/>
设置为 1 以启用超越数学浮点库函数在 X64 上 FMA3 实现平台，或为 0，以使用不使用 FMA3 指令的实现。

## <a name="return-value"></a>返回值

如果启用超越数学浮点库函数的 FMA3 实现了一个非零值。 否则为为零。

## <a name="remarks"></a>备注

使用 **_set_FMA3_enable**函数来启用或禁用在 CRT 库中的超越数学浮点函数的 FMA3 指令的使用。 返回值反映了在使用更改后的实现。 如果 CPU 不支持 FMA3 指令，此函数不能启用它们在库中，并返回值为零。 使用 **_get_FMA3_enable**获取库的当前状态。 默认情况下，在 X64 平台，CRT 启动代码检测到 CPU 支持 FMA3 指令和启用或禁用库中的 FMA3 实现。

FMA3 实现使用不同的算法，因此，略有差异的计算结果可能是可观察量时 FMA3 实现启用或禁用，或执行操作或不支持 FMA3 的计算机之间。 有关详细信息，请参阅[浮点迁移问题](../../porting/floating-point-migration-issues.md)。

## <a name="requirements"></a>要求

**_Set_FMA3_enable**并 **_get_FMA3_enable**函数是仅提供 X64 版本的 CRT。

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_FMA3_enable**， **_get_FMA3_enable**| C：\<math.h><br />C++: \<cmath > 或\<math.h >|

**_Set_FMA3_enable**并 **_get_FMA3_enable**是 Microsoft 特定函数的函数。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[浮点迁移问题](../../porting/floating-point-migration-issues.md)<br/>
