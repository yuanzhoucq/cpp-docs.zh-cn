---
title: /Q 选项（低级别操作）
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: a6dcbd256fa3510955884d3adba4855b23cdbfab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514242"
---
# <a name="q-options-low-level-operations"></a>/Q 选项（低级别操作）

可以使用 **/Q**编译器选项来执行以下低级别编译器操作：

- [/Qfast_transcendentals （强制快速先验）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)： 生成快速先验。

- [/Qifist (取消 _ftol)](../../build/reference/qifist-suppress-ftol.md)： 取消`_ftol`时从浮点类型转换为整数类型是必需 (仅限 x86)。

- [/Qimprecise_fwaits （移除 Try 块中的 fwaits）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)： 移除`fwait`内的命令`try`块。

- [/Qpar （自动并行化程序）](../../build/reference/qpar-auto-parallelizer.md)： 启用自动并行化的循环标有[#pragma loop （)](../../preprocessor/loop.md)指令。

- [/Qpar-report （自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)： 启用自动并行化的报告级别。

- [/Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)： 禁止优化的浮点寄存器加载和有关内存和 MMX 之间移动注册。

- [/Qspectre](../../build/reference/qspectre.md)： 生成指令以缓解特定 Spectre 安全漏洞。

- [/Qvec-report （自动矢量化程序报告等级）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)： 启用自动矢量化的报告级别。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
