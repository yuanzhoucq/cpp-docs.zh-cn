---
title: /guard:ehcont（启用 EH 持续元数据）
description: Microsoft c + +/guard： ehcont 编译器选项的参考指南。
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: 0c5a49d578e626d052aa9d132afbaee5686cb7a7
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520520"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>/guard:ehcont（启用 EH 持续元数据）

通过编译器启用 EH 继续（EHCONT）元数据的生成。

## <a name="syntax"></a>语法

> **`/guard:ehcont`**[**`-`**]

## <a name="remarks"></a>备注

**`/guard:ehcont`** 选项会使编译器生成一个排序列表，其中列出了二进制文件的所有有效异常处理延续目标的相对虚拟地址（RVA）。 它在运行时用于 `NtContinue` 和 `SetThreadContext` 指令指针验证。 默认情况下， **`/guard:ehcont`** 处于关闭状态，必须显式启用。 若要显式禁用此选项，请使用 **`/guard:ehcont-`** 。

此 **`/guard:ehcont`** 选项在 Visual Studio 2019 版本16.7 及更高版本中可用。 64位操作系统上的64位进程支持此功能。

[控制流强制技术（CET）](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)是一种基于硬件的安全功能，可防止基于返回编程（ROP）的攻击。 它为每个调用堆栈维护一个 "阴影堆栈"，以强制实施控制流完整性。

当有可用的卷影堆栈来防止 ROP 攻击时，攻击者会继续使用其他利用方法。 它们可能使用的一种方法是损坏[上下文](/windows/win32/api/winnt/ns-winnt-context)结构内的指令指针值。 此结构传递到重定向线程执行的系统调用，如 `NtContinue` 、 [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) 和 [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) 。 `CONTEXT`结构存储在内存中。 损坏它包含的指令指针可能会导致系统调用将执行传输到攻击者控制的地址。 目前， `NTContinue` 可以通过任何延续点来调用。 这就是在启用影子堆栈时验证指令指针至关重要的原因。

`RtlRestoreContext``NtContinue`在结构化异常处理（SEH）异常展开过程中，将使用和来展开到包含该块的目标框架 **`__except`** 。 块的指令指针 **`__except`** 不应位于阴影堆栈上，因为这会导致指令指针验证失败。 **`/guard:ehcont`** 编译器开关生成 "EH 延续表"。 它包含二进制文件中所有有效异常处理延续目标的 Rva 的排序列表。 `NtContinue`首先检查用户提供的指令指针的阴影堆栈，并且如果在此处找不到指令指针，它将继续检查包含指令指针的二进制文件中的 EH 延续表。 如果包含的二进制文件未使用表编译，则允许继续进行与旧版二进制文件的兼容性 `NtContinue` 。 很重要的一点是，区分没有 EHCONT 数据的旧二进制文件和包含 EHCONT 数据但没有表条目的二进制文件。 前者允许二进制文件中的所有地址都是有效的继续目标。 后者不允许二进制文件中的任何地址作为有效的延续目标。

**`/guard:ehcont`** 必须将选项传递给编译器和链接器以生成适用于二进制的 EH 继续目标 rva。 如果你的二进制文件是使用单个 `cl` 命令生成的，则编译器会将该选项传递到链接器。 编译器还会将 [**`/guard:cf`**](guard-enable-control-flow-guard.md) 选项传递到链接器。 如果单独编译和链接，则必须同时在编译器和链接器命令上设置这些选项。

您可以将使用编译的代码链接 **`/guard:ehcont`** 到不使用它编译的库和对象文件。 在以下任一情况下，链接器都将返回错误：

- 代码段包含 "本地展开"。 有关详细信息，请参阅[try-Finally 语句](../../cpp/try-finally-statement.md#abnormal-termination)中的异常终止。

- EH （xdata）部分包含指向代码部分的指针，并且它们不用于 SEH。

- 指针适用于 SEH，但没有使用函数级链接（[/gy](gy-enable-function-level-linking.md)）编译对象文件以生成 comdat。

链接器将返回错误，因为它无法在这些情况下生成元数据。 这意味着引发异常可能会导致运行时崩溃。

对于在 Comdat 中找到但未使用编译的 SEH 节信息 **`/guard:ehcont`** ，链接器发出警告**LNK4291**。 在这种情况下，链接器将为节生成正确但保守的元数据。 若要忽略此警告，请使用[/IGNORE （忽略特定警告）](ignore-ignore-specific-warnings.md)。

如果链接器无法生成元数据，则会发出以下错误之一：

- `LNK2046: module contains _local_unwind but was not compiled with /guard:ehcont`

- `LNK2047: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

若要检查二进制文件是否包含 EHCONT 数据，请在转储二进制文件的负载配置时查找以下元素：

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **代码生成**" 属性页。

1. 选择 "**启用 EH 继续元数据**" 属性。

1. 在下拉控件中，选择 **"是" （/guard： ehcont）** 启用 EH 继续元数据，或选择 "**否" （/guard： ehcont-）** 以禁用它。

## <a name="see-also"></a>请参阅

[/guard （启用控制流防护）](guard-enable-control-flow-guard.md)\
[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
