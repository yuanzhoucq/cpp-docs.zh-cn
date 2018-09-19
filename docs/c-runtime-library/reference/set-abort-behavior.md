---
title: _set_abort_behavior | Microsoft 文档
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 299801cc4276118fc73a4be625a3df8cc84d58b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692929"
---
# <a name="setabortbehavior"></a>_set_abort_behavior

指定当程序异常终止时要采取的操作。

> [!NOTE]
> 不要使用[中止](abort.md)函数来关闭的情况下的 Microsoft Store 应用，除非在测试或调试方案。 以编程或 UI 方式关闭应用商店应用程序不允许根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)。 有关详细信息，请参阅[UWP 应用程序生命周期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>语法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>参数

*flags*<br/>
新值[中止](abort.md)标志。

*掩码*<br/>
掩码[中止](abort.md)标志位设置。

## <a name="return-value"></a>返回值

标志的旧值。

## <a name="remarks"></a>备注

有两个[中止](abort.md)标志： **_WRITE_ABORT_MSG**并 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**确定当程序异常终止时是否打印有帮助的文本消息。 该消息声明应用程序已调用[中止](abort.md)函数。 默认行为是打印该消息。 **_CALL_REPORTFAULT**，如果设置，则指定 Watson 故障转储生成和报告何时[中止](abort.md)调用。 默认情况下，在非调试生成中启用故障转储报告。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[abort](abort.md)<br/>
