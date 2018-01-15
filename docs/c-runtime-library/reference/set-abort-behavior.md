---
title: "_set_abort_behavior | Microsoft 文档"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_abort_behavior
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
dev_langs: C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 965ff160fd8098c60f53f639cb95aedf890edd86
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2018
---
# <a name="setabortbehavior"></a>_set_abort_behavior

指定当程序异常终止时要采取的操作。

> [!NOTE]
> 不要使用`abort`函数可以在测试或调试方案中关闭除 Microsoft 应用商店应用。 编程或 UI 方式关闭应用商店应用程序不允许根据[Microsoft 存储策略](http://go.microsoft.com/fwlink/?LinkId=865936)。 有关详细信息，请参阅[UWP 应用生命周期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

## <a name="syntax"></a>语法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>参数

[in]_标志_  
`abort` 标志的新值。

[in]_掩码_  
要设置的 `abort` 标志位掩码。

## <a name="return-value"></a>返回值

标志的旧值。

## <a name="remarks"></a>备注

有两个 `abort` 标志：`_WRITE_ABORT_MSG` 和 `_CALL_REPORTFAULT`。 `_WRITE_ABORT_MSG` 确定在程序异常终止时是否打印有帮助的文本信息。 该消息声明应用程序已调用 `abort` 函数。 默认行为是打印该消息。 如果设置 `_CALL_REPORTFAULT`，则指定在调用 `abort` 时生成和报告 Watson 故障转储。 默认情况下，在非调试生成中启用故障转储报告。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_set_abort_behavior`|\<stdlib.h>|

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

[abort](../../c-runtime-library/reference/abort.md)  
