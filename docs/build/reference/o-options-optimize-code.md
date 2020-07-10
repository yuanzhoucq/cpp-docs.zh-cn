---
title: /O 选项（优化代码）
description: MSVC/O 编译器选项指定要使用的编译器优化。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: 36ef582787a3ec2d7aee1e589c70b48712d9d552
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180872"
---
# <a name="o-options-optimize-code"></a>`/O` (优化代码的选项) 

这些 **`/O`** 选项控制各种优化，可帮助你创建最大速度或最小大小的代码。

- [`/O1`](o1-o2-minimize-size-maximize-speed.md)设置生成最小大小代码的优化组合。

- [`/O2`](o1-o2-minimize-size-maximize-speed.md)设置优化的优化的组合，以最大速度优化代码。

- [`/Ob`](ob-inline-function-expansion.md)控制内联函数展开。

- [`/Od`](od-disable-debug.md)禁用优化，加快编译速度并简化调试。

- [`/Og`](og-global-optimizations.md) (弃用) 启用全局优化。

- [`/Oi`](oi-generate-intrinsic-functions.md)为适当的函数调用生成内部函数。

- [`/Os`](os-ot-favor-small-code-favor-fast-code.md)指示编译器优选大小优化以优化速度。

- [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) (默认设置) 通知编译器优选速度优化以优化大小的优化。

- [`/Ox`](ox-full-optimization.md)组合选项，可选择多个优化并注重速度。 **`/Ox`** 是优化的严格子集 **`/O2`** 。

- [`/Oy`](oy-frame-pointer-omission.md)禁止在调用堆栈上创建帧指针，以便更快地调用函数。

## <a name="remarks"></a>备注

可以将多个 **`/O`** 选项组合到一个选项语句中。 例如，与 **`/Odi`** 相同 **`/Od /Oi`** 。 某些选项是互斥的，如果一起使用，则会引发编译器错误。 有关详细信息，请参阅各个 **`/O`** 选项。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
