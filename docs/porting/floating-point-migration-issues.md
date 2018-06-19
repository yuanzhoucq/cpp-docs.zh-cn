---
title: 浮点迁移问题 | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e6578486ada758482b270cd5505338e2acf3eb9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841897"
---
# <a name="floating-point-migration-issues"></a>浮点迁移问题  
  
有时将项目升级到较新版本的 Visual Studio 后，可能会发现某些浮点操作的结果已更改。 出现这种情况通常由以下两个原因之一引起：为了更好地利用提供的处理器而进行的代码生成更改；C 运行时库 (CRT) 中数学函数所使用的算法的 bug 修复或更改。 一般情况下，新的结果在语言标准指定的限制范围内是正确的。 请继续阅读，了解更改的内容，如果重要，请了解如何获得函数之前获得的同一结果。  

## <a name="new-math-functions-and-universal-crt-changes"></a>新的数学函数和通用的 CRT 更改  
  
多年来 Visual Studio 中提供了大多数的 CRT 数学函数，但从 Visual Studio 2013 开始，将包括 ISO C99 要求的所有函数。 这些函数的实现是为了平衡性能与正确性。 因为在每个用例中产生正确舍入的结果可能成本过高，这些函数旨在有效地生成接近正确舍入结果的近似结果。 在大多数情况下，虽然可能存在误差较大的情况，但生成的结果在正确舍入结果的 +/-1 最小精度单位或 ulp 范围内。 如果之前使用不同的数学库获取这些函数，实现差异可能会引起结果发生更改。   
    
数学函数移到 Visual Studio 2015 中的通用 CRT 后，使用了一些新的算法并修复了 Visual Studio 2013 中新增函数的实现中的多个 bug。 这些更改可能在使用这些函数的浮点计算结果中产生可检测差异。 具有 bug 问题的函数有 erf、exp2、remainder、remquo、scalbln、scalbn 及其浮点型和长双精度型变体。  Visual Studio 2015 中的其他更改修复了保留 _clear87、_clearfp、fegetenv、fesetenv 和 feholdexcept 函数中浮点状态字和异常状态信息的问题。  
  
## <a name="processor-differences-and-compiler-flags"></a>处理器差异和编译器标志  
  
许多浮点数学库函数具有不同 CPU 体系结构的不同实现。 例如，相比 64 位 x64 CRT，32 位 x86 CRT 可能具有不同的实现。 此外，某些函数可能有适用于给定 CPU 体系结构的多个实现。 在运行时动态地选择最有效的实现，具体取决于受 CPU 支持的指令集。 例如，在 32 位 x86 CRT 中，一些函数同时具有 x87 实现和 SSE2 实现。 在支持 SSE2 的 CPU 上运行时，使用速度更快的 SSE2 实现。 在不支持 SSE2 的 CPU 上运行时，使用速度较慢的 x87 实现。 迁移旧代码时可能会看到，因为 Visual Studio 2012 中默认的 x86 编译器体系结构选项已更改为 [/arch:SSE2](../build/reference/arch-x86.md)。 数学库函数的不同实现可能会使用不同的 CPU 指令和不同的算法来生成其结果，因此，这些函数可能会在各平台上产生不同的结果。 在大多数情况下，结果在正确舍入结果的 +/-1 ulp 范围内，但实际结果在各 CPU 中可能会有所不同。  
  
将旧代码与新代码比较时，甚至在使用同一编译器标志时，Visual Studio 中不同的浮动点模式下提高代码生成的正确性也会影响浮点运算的结果。 例如，指定 [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md)（默认值）或 **/fp:strict** 时，Visual Studio 2010 生成的代码可能未通过表达式正确传播中间非数字 (NaN) 值。 因此，在较旧的编译器中产生数值结果的某些表达式现在可能会产生正确的 NaN 结果。 你还可能看到差异，因为针对 **/fp:fast** 启用的代码优化现能够利用更多处理器功能。 这些优化可以使用更少的说明，但可能会影响生成的结果，因为某些先前可见的中间操作已删除。  
  
## <a name="how-to-get-identical-results"></a>如何获得相同的结果  
  
在大多数情况下，最新的编译器和库中的浮点更改的行为更快和/或更正确。 当 SSE2 指令替换 x87 说明时，你甚至可以看到更优秀的处理器性能。 但是，如果代码必须精确复制较旧编译器的浮点行为，请考虑使用 Visual Studio 本机多重目标功能，并使用较旧的工具集生成受影响的项目。 有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](use-native-multi-targeting.md)。  
  
## <a name="see-also"></a>请参阅  
  
[从 Visual C++ 早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[潜在的升级问题概述 (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Visual C++ 更改历史记录（2003 - 2015）](visual-cpp-change-history-2003-2015.md)  
