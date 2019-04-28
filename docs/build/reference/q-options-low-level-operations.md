---
title: /Q 选项（低级别操作）
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 5bbb63b4f437f8aefd5c84c1c1c4bd20bdb965cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319377"
---
# <a name="q-options-low-level-operations"></a>/Q 选项（低级别操作）

可以使用 **/Q**编译器选项来执行以下低级别编译器操作：

- [/Qfast_transcendentals （强制快速先验）](qfast-transcendentals-force-fast-transcendentals.md):生成快速先验。

- [/Qifist （取消 _ftol）](qifist-suppress-ftol.md):禁止显示`_ftol`时从浮点类型转换为整数类型是必需 (仅限 x86)。

- [/Qimprecise_fwaits （移除 Try 块中的 fwaits）](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md):移除 `fwait` 块中的 `try` 命令。

- [/Qpar （自动并行化程序）](qpar-auto-parallelizer.md):对标记有 [#pragma loop()](../../preprocessor/loop.md) 指令的循环启用自动并行化。

- [/Qpar-report （自动并行化程序报告等级）](qpar-report-auto-parallelizer-reporting-level.md):启用自动并行化的报告级别。

- [/Qsafe_fp_loads](qsafe-fp-loads.md):禁止针对浮点寄存器负载和有关内存和 MMX 寄存器之间移动的优化。

- [/Qspectre](qspectre.md):生成以缓解特定 Spectre 安全漏洞的指导。

- [/Qvec-report （自动矢量化程序报告等级）](qvec-report-auto-vectorizer-reporting-level.md):启用自动矢量化的报告级别。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
