---
title: /Zm（指定预编译标头的内存分配限额）
ms.date: 03/08/2019
f1_keywords:
- /zm
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
ms.openlocfilehash: 3c1362479b2068ee8fb527a4ecaac6e203e83cb0
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751981"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm（指定预编译标头的内存分配限额）

确定编译器分配的用于构造预编译标头的内存量。

## <a name="syntax"></a>语法

```
/Zmfactor
```

## <a name="arguments"></a>自变量

*factor*<br/>
一个比例因子，确定编译器用于构造预编译标头的内存量。

*身份*自变量是编译器定义的工作缓冲区默认大小的百分比。 默认值*身份*为 100 （%），但您可以指定更大或较小数量。

## <a name="remarks"></a>备注

在 Visual Studio 2015 之前的版本，c + + 编译器使用几个离散堆，每个有一定的限制。 目前，编译器将动态增加堆，最大总堆大小限制，有必要，允许预编译标头以包含多个地址范围。 因此， **/Zm**编译器选项很少需要。

如果编译器用完堆空间，并发出[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)使用时，错误消息 **/Zm**编译器选项，您可能保留了太多内存。 请考虑删除 **/Zm**选项。

如果编译器发出[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)错误消息，则伴随[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)消息指定*身份*参数时使用重新编译使用 **/Zm**编译器选项。 预编译标头使用时，此消息只是重要`#pragma hdrstop`。 在其他情况下，是虚假错误引起的 Windows 虚拟内存不足问题和建议使用 **/Zm**应忽略选项。 相反，请考虑减少使用时的并行进程数 **/maxcpucount** MSBUILD 选项。结合 EXE **/MP**改为 CL 选项。EXE。 有关详细信息，请参阅[预编译标头 (PCH) 问题和建议](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)。

下表显示如何*身份*参数会影响内存分配限制，如果你假定默认预编译标头缓冲区的大小为 75 MB。

|值*身份*|内存分配限制|
|-----------------------|-----------------------------|
|10|7.5 MB|
|100|75 MB|
|200|150 MB|
|1000|750 MB|
|2000|1500 MB|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>设置内存分配限制的其他方式

### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 /Zm 编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 在导航窗格中，选择**配置属性** > **C/c + +** > **命令行**。

1. 输入 **/Zm**中的编译器选项**其他选项**框。

### <a name="to-set-the-zm-compiler-option-programmatically"></a>以编程方式设置 /Zm 编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
