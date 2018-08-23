---
title: fegetround、 fesetround |Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
dev_langs:
- C++
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 137d886d557cbb1fee7db1dd60405b9557bf6bf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398079"
---
# <a name="fegetround-fesetround"></a>fegetround、fesetround

获取或设置当前的浮点舍入模式。

## <a name="syntax"></a>语法

```C
int fegetround(void);

int fesetround(
   int round_mode
);
```

### <a name="parameters"></a>参数

*round_mode*<br/>
要作为其中一个浮点舍入宏设置的舍入模式。 如果该值不等于其中一个浮点舍入宏，则舍入模式不会更改。

## <a name="return-value"></a>返回值

如果成功， **fegetround**作为其中一个浮点舍入宏值返回舍入模式。 如果无法确定当前的舍入模式，它返回一个负值。

如果成功， **fesetround**返回 0。 否则，返回一个非零值。

## <a name="remarks"></a>备注

浮点运算可以使用数种舍入模式中的其中一种。 这些模式控制存储结果时浮点运算结果的舍入方向。 以下是在 \<fenv.h> 中定义的浮点舍入宏的名称和行为：

|宏|描述|
|-----------|-----------------|
|FE_DOWNWARD|向负无穷舍入。|
|FE_TONEAREST|向最近一方舍入。|
|FE_TOWARDZERO|向零舍入。|
|FE_UPWARD|向正无穷舍入。|

FE_TONEAREST 的默认行为是要将结果从可表示值的中间向具有偶数 (0) 最低有效位的最近值舍入。

当前舍入模式将影响以下操作：

- 字符串转换

- 常量表达式之外的浮点算术运算符的结果。

- 库舍入函数，如**rint**和**nearbyint**。

- 从标准库的数学函数返回的值。

当前舍入模式不影响以下操作：

- **Trunc**， **ceil**， **floor**，和**lround**库函数。

- 浮点到整数隐式强制转换和转换，始终向零舍入。

- 常量表达式中浮点算术运算符的结果，始终舍入到最接近的值。

若要使用这些函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fegetround**， **fesetround**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint、rintf、rintl](rint-rintf-rintl.md)<br/>
[lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
