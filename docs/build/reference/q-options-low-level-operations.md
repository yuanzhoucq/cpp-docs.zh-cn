---
title: -Q 选项 （低级别操作） |Microsoft 文档
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /q
dev_langs:
- C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a18c5d790cf21e8eb130a2b2baa152e20d79a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375030"
---
# <a name="q-options-low-level-operations"></a>/Q 选项（低级别操作）

你可以使用 **/Q**编译器选项执行以下低级别编译器操作：

- [/Qfast_transcendentals （强制快速先验）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)： 生成快速先验。

- [/Qifist (取消 _ftol)](../../build/reference/qifist-suppress-ftol.md)： 取消`_ftol`从浮点类型转换为整型时必需 (仅限 x86)。

- [/Qimprecise_fwaits （移除 Try 块中的 fwaits）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)： 删除`fwait`内的命令`try`块。

- [/Qpar （自动并行化）](../../build/reference/qpar-auto-parallelizer.md)： 启用自动并行化的循环标记有[#pragma loop （)](../../preprocessor/loop.md)指令。

- [/Qpar-report （自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)： 启用自动并行化的报告级别。

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)： 取消优化，为浮点寄存器加载并为内存和 MMX 之间移动注册。

- [/ Qspectre](../../build/reference/qspectre.md)： 时会生成一些指令，以缓解特定 Spectre 安全漏洞。

- [/Qvec-report （自动向量化报告等级）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)： 启用自动矢量化的报告级别。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
