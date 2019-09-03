---
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: 34198409c6a57eb494bfe819b367b71405a84e64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222199"
---
# <a name="__fastfail"></a>__fastfail

**Microsoft 专用**

立即终止开销最少的调用过程。

## <a name="syntax"></a>语法

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>参数

*编写*\
中一个`FAST_FAIL_<description>`来自 winnt 或 wdm 的符号常量, 用于指示进程终止的原因。

## <a name="return-value"></a>返回值

`__fastfail` 内部函数不会返回。

## <a name="remarks"></a>备注

内部函数为*快速失败*请求提供了一种机制, 这种方法可能会损坏进程请求立即终止进程。 `__fastfail` 无法使用常规异常处理设施处理可能已破坏程序状态和堆栈至无法恢复的的严重故障。 使用 `__fastfail` 终止开销最少的进程。

在内部，可以使用几个特定于体系结构的机制实现 `__fastfail`：

|体系结构|指令|代码参数的位置|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|`ecx`|
|X64|int 0x29|`rcx`|
|ARM|操作码 0xDEFB|`r0`|
|ARM64|Opcode 0xF003|`x0`|

快速失败请求是独立的请求，通常只需执行两个指令。 执行快速失败请求后, 内核会执行相应的操作。 在用户模式代码中，引发速快速失败事件时，除指令指针本身外不存在任何内存依赖项。 这可最大程度地提高其可靠性, 即使是在出现严重内存损坏的情况下。

自变量、winnt 或 wdm `FAST_FAIL_<description>`中的符号常量之一描述故障条件的类型。 `code` 它以特定于环境的方式纳入故障报告。

用户模式快速失败请求显示为第二次机会非持续性异常, 异常代码为 0xC0000409, 至少有一个异常参数。 第一个异常参数为 `code` 值。 此异常代码向 Windows 错误报告 (WER) 和调试基础结构指示进程已损坏, 并且应采取最少的进程内操作来响应故障。 内核模式快速失败请求可以通过使用专用检错代码 `KERNEL_SECURITY_CHECK_FAILURE` (0x139) 实现。 在这两种情况下，都没有调用异常处理程序，因为程序预期处于损坏状态。 如果存在调试器, 它将有机会在终止前检查程序的状态。

Windows 8 开始支持本机快速失败机制。 不支持本机快速失败指令的 Windows 操作系统通常会将快速失败请求视为访问冲突或`UNEXPECTED_KERNEL_MODE_TRAP`错误检测。 在这些情况下，仍然会终止程序，但并不一定会快速终止。

`__fastfail` 只能用作内部函数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__fastfail`|x86、x64、ARM、ARM64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
