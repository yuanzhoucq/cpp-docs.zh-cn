---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: 06f72597a384cc5c90b2e345e62e13dee96c4dca
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913133"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

指定当程序异常终止时要采取的操作。

> [!NOTE]
> 不要使用[abort](abort.md)函数关闭 Microsoft Store 的应用程序，除非在测试或调试方案中。 根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)，不允许以编程方式或 UI 方式关闭应用商店应用。 有关详细信息，请参阅[UWP 应用生命周期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>语法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>参数

*flag*<br/>
[中止](abort.md)标志的新值。

*掩码*<br/>
要设置的[中止](abort.md)标志位的掩码。

## <a name="return-value"></a>返回值

标志的旧值。

## <a name="remarks"></a>备注

有两种[中止](abort.md)标志： **_WRITE_ABORT_MSG**和 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**确定在程序异常终止时是否打印有帮助的文本消息。 此消息表明应用程序已调用[abort](abort.md)函数。 默认行为是打印该消息。 **_CALL_REPORTFAULT**（如果已设置）指定在调用[abort](abort.md)时生成并报告 Watson 故障转储。 默认情况下，在非调试生成中启用故障转储报告。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>另请参阅

[中止](abort.md)<br/>
