---
title: _execute_onexit_table、_initialize_onexit_table、_register_onexit_function |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs:
- C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9a6ea61883e6ce94bc41f16e7139156c68c8059
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082087"
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table、_initialize_onexit_table、_register_onexit_function

管理在退出时要调用的例程。

## <a name="syntax"></a>语法

```
int _initialize_onexit_table(
    _onexit_table_t* table
    );

int _register_onexit_function(
    _onexit_table_t* table,
    _onexit_t        function
    );

int _execute_onexit_table(
    _onexit_table_t* table
    );
```

#### <a name="parameters"></a>参数

*table*<br/>
[in, out] 指向 onexit 函数表的指针。

*函数*<br/>
[in] 指向一个函数以添加到 onexit 函数表的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 否则，返回一个负值。

## <a name="remarks"></a>备注

这些函数是用来支持 C 运行时的基础结构实现详细信息，不应在代码中直接调用。 C 运行时使用 *onexit 函数表*来表示通过调用 `atexit`、`at_quick_exit`，和 `_onexit` 注册的函数序列。 onexit 函数表数据结构是 C 运行时的非跳转实现详细信息；可以更改此数据成员的顺序和含义。 它们不应由外部代码进行检查。

`_initialize_onexit_table` 函数将 onexit 函数表初始化为其初始值。  将 onexit 函数表传递给 `_register_onexit_function` 或 `_execute_onexit_table` 前，必须调用此函数。

`_register_onexit_function` 函数在 onexit 函数表的末尾追加一个函数。

`_execute_onexit_table` 函数执行 onexit 函数表中的所有函数，并清除表，然后返回。 在调用 `_execute_onexit_table` 后，表处于无效状态；必须通过调用 `_initialize_onexit_table` 以对其重新初始化后才能再次使用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|

`_initialize_onexit_table`、`_register_onexit_function` 和 `_execute_onexit_table` 函数是 Microsoft 特定函数。 有关兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)