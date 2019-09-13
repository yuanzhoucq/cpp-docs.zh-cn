---
title: /Q 选项（低级别操作）
ms.date: 01/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 6348226aa38d1f2eefdf9e19e27c4c87bd2f0812
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927674"
---
# <a name="q-options-low-level-operations"></a>/Q 选项（低级别操作）

您可以使用 **/q**编译器选项来执行以下底层编译器操作：

- [/Qfast_transcendentals （强制快速先验）](qfast-transcendentals-force-fast-transcendentals.md)：生成快速先验。

- [/QIfist （取消 _ftol）](qifist-suppress-ftol.md)：当`_ftol`需要从浮点类型到整数类型的转换时，禁止使用（仅限 x86）。

- [/Qimprecise_fwaits （删除 Fwaits 在 Try 块内）](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)：移除 `fwait` 块中的 `try` 命令。

- [/Qpar （自动并行）](qpar-auto-parallelizer.md)：对标记有 [#pragma loop()](../../preprocessor/loop.md) 指令的循环启用自动并行化。

- [/Qpar-report （自动并行报告级别）](qpar-report-auto-parallelizer-reporting-level.md)：启用自动并行化的报告级别。

- [/Qsafe_fp_loads](qsafe-fp-loads.md)：禁止对浮点寄存器负载进行优化，以及在内存和 MMX 寄存器之间移动。

- [/Qspectre](qspectre.md)：生成缓解某些 Spectre 安全漏洞的说明。

- [/Qvec-report （自动向量化报告级别）](qvec-report-auto-vectorizer-reporting-level.md)：启用自动矢量化的报告级别。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
