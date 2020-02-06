---
title: /Qspectre-load
description: 描述 Microsoft C/C++编译器（MSVC）/Qspectre-load 选项。
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load
ms.openlocfilehash: a766cf9b7eef11b7c5819cbdaa7706ab5b80c608
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035552"
---
# <a name="qspectre-load"></a>/Qspectre-load

指定编译器对每个加载指令序列化指令的生成。 此选项扩展了 **/Qspectre**标志，从而减轻了基于负载的任何可能的**推理执行方通道攻击**。

## <a name="syntax"></a>语法

> **/Qspectre-load**

## <a name="remarks"></a>备注

**/Qspectre-load**导致编译器检测内存中的负载，并在其后面插入序列化说明。 加载内存（包括 `RET` 和 `CALL`）的控制流指令拆分为负载和控制流传输。 负载后跟一个 `LFENCE` 以确保负载受到保护。 在某些情况下，编译器无法拆分控制流指令（如 `jmp` 指令），因此它使用备用的缓解技术。 例如，在插入 LFENCE 之前，编译器会通过添加指令以非破坏性方式来缓解 `jmp [rax]`，如下所示：

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

由于 **/Qspectre-load**停止所有加载的推理，因此性能影响很高。 缓解措施并不合适。 如果有性能关键的代码块不需要保护，则可以使用 `__declspec(spectre(nomitigation))`禁用这些缓解措施。 有关详细信息，请参阅[__declspec spectre](../../cpp/spectre.md)。

默认情况下， **/Qspectre-load**选项为 off，并支持所有优化级别。

Visual Studio 2019 版本16.5 及更高版本中提供了 **/Qspectre-load**选项。 此选项仅适用于面向 x86 和 x64 处理器的编译器。 它在面向 ARM 处理器的编译器中不可用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

2. 选择 "**配置属性**" > " **C/C++**  > **代码生成**" 属性页。

3. 为**Spectre 缓解**属性选择一个新值。 选择“确定”应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)\
[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
