---
title: runtime_checks 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: a1c8e6cca27e157818e6ec80182f8fefa112daf1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216616"
---
# <a name="runtime_checks-pragma"></a>runtime_checks 杂注

禁用或还原 [/RTC](../build/reference/rtc-run-time-error-checks.md) 设置。

## <a name="syntax"></a>语法

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **restore** | **off** } **)**

## <a name="remarks"></a>备注

不能启用由编译器选项启用的运行时检查。 例如, 如果未在命令行`/RTCs`上指定, 则指定`#pragma runtime_checks( "s", restore)`将不会启用堆栈帧验证。

**Runtime_checks**杂注必须出现在函数的外部, 并在出现杂注后定义的第一个函数处生效。 **restore** 和 **off** 参数打开或关闭 **runtime_checks** 中指定的选项。

**runtime_checks** 可以为下表中显示的零个或多个参数。

### <a name="parameters-of-the-runtime_checks-pragma"></a>runtime_checks 杂注的参数

| 参数 | 运行时检查的类型 |
|--------------------|-----------------------------|
| **秒** | 启用堆栈（帧）验证。 |
| **c** | 报告何时向较小的数据类型赋值会导致数据丢失。 |
| **u** | 报告变量在定义之前的使用情况。 |

这些参数与`/RTC`编译器选项一起使用的参数相同。 例如：

```cpp
#pragma runtime_checks( "sc", restore )
```

将 **runtime_checks** 杂注和空字符串 ( **""** ) 一起使用是该指令的特殊形式：

- 当使用**off**参数时, 它将关闭上表中列出的运行时错误检查。

- 使用**restore**参数时, 它会将运行时错误检查重置为你使用`/RTC`编译器选项指定的检查。

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
