---
title: _execute_onexit_table、_initialize_onexit_table、_register_onexit_function
ms.date: 4/2/2020
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
- _o__execute_onexit_table
- _o__initialize_onexit_table
- _o__register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
ms.openlocfilehash: a1e35d9e86a43e48849373a1cf1aa07febcd0e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351644"
---
# <a name="_execute_onexit_table-_initialize_onexit_table-_register_onexit_function"></a>_execute_onexit_table、_initialize_onexit_table、_register_onexit_function

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

*表*<br/>
[in, out] 指向 onexit 函数表的指针。

*功能*<br/>
[in] 指向一个函数以添加到 onexit 函数表的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 否则，返回一个负值。

## <a name="remarks"></a>备注

这些函数是用来支持 C 运行时的基础结构实现详细信息，不应在代码中直接调用。 C 运行时使用*onexit 函数表*来表示由 调用 注册`atexit``at_quick_exit`的函数序列 。 `_onexit` onexit 函数表数据结构是 C 运行时的非跳转实现详细信息；可以更改此数据成员的顺序和含义。 它们不应由外部代码进行检查。

`_initialize_onexit_table` 函数将 onexit 函数表初始化为其初始值。  将 onexit 函数表传递给 `_register_onexit_function` 或 `_execute_onexit_table` 前，必须调用此函数。

`_register_onexit_function` 函数在 onexit 函数表的末尾追加一个函数。

`_execute_onexit_table` 函数执行 onexit 函数表中的所有函数，并清除表，然后返回。 在调用 `_execute_onexit_table` 后，表处于无效状态；必须通过调用 `_initialize_onexit_table` 以对其重新初始化后才能再次使用。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|

`_register_onexit_function``_execute_onexit_table`和`_initialize_onexit_table`函数特定于 Microsoft。 有关兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
