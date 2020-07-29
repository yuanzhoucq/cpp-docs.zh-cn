---
title: /Q 选项（低级别操作）
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: f5342071cef76bcc736f128c344279898a61c462
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231489"
---
# <a name="q-options-low-level-operations"></a>/Q 选项（低级别操作）

您可以使用 **/q**编译器选项来执行以下底层编译器操作：

- [/Qfast_transcendentals （强制 Fast 先验）](qfast-transcendentals-force-fast-transcendentals.md)：生成快速先验。

- [/QIfist （取消 _ftol）](qifist-suppress-ftol.md)：取消 `_ftol` 从浮点类型到整数类型的转换（仅限 x86）。

- [/Qimprecise_fwaits （在 Try 块内删除 fwaits）](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)：删除 `fwait` **`try`** 块中的命令。

- [/QIntel-jcc-erratum](qintel-jcc-erratum.md)：缓解由 Intel 跳转条件代码（jcc）错误微代码更新导致的性能影响。

- [/Qpar （自动并行）](qpar-auto-parallelizer.md)：启用标记为[#pragma loop （）](../../preprocessor/loop.md)指令的循环的自动并行化。

- [/Qpar-report （自动并行报告级别）](qpar-report-auto-parallelizer-reporting-level.md)：启用自动并行化的报告级别。

- [/Qsafe_fp_loads](qsafe-fp-loads.md)：取消对浮点寄存器负载和在内存和 MMX 寄存器之间移动的优化。

- [/Qspectre](qspectre.md)：生成缓解某些 Spectre 安全漏洞的说明。

- [/Qspectre-load](qspectre-load.md)：根据负载生成用于缓解 Spectre 安全漏洞的说明。

- [/Qspectre-load-cf](qspectre-load-cf.md)：根据负载的控制流指令生成用于缓解 Spectre 安全漏洞的说明。

- [/Qvec-report （自动向量化报告级别）](qvec-report-auto-vectorizer-reporting-level.md)：为自动矢量化启用报表级别。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
