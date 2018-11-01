---
title: /O 选项（优化代码）
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: f4e2bf8b848654f7b87c59e7a54994448ee62d51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481302"
---
# <a name="o-options-optimize-code"></a>/O 选项（优化代码）

**/O**选项可控制各种优化，可帮助您创建代码的最大速度或最小大小。

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)设置组合生成最小大小代码的优化。

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)设置为最大速度优化代码的优化组合。

- [/Ob](../../build/reference/ob-inline-function-expansion.md)控制内联函数展开。

- [/Od](../../build/reference/od-disable-debug.md)禁用优化，可以加快编译和简化调试。

- [/Og](../../build/reference/og-global-optimizations.md)启用全局优化。

- [/Oi](../../build/reference/oi-generate-intrinsic-functions.md)为适当的函数调用生成内部函数。

- [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)告知编译器优选速度优化大小。

- [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) （默认设置） 将告知编译器优选大小优化的速度。

- [/Ox](../../build/reference/ox-full-optimization.md)是一个组合选项，选择多个侧重于速度优化。 是的严格子集 **/o2**优化。

- [/Oy](../../build/reference/oy-frame-pointer-omission.md)取消帧指针更快地函数调用在调用堆栈上创建。

## <a name="remarks"></a>备注

你可以组合多个 **/O**到单个选项语句的选项。 例如， **/Odi**等同于 **/Od /Oi**。 某些选项相互排斥，如果一起使用会导致编译器错误。 请参阅各个 **/O**选项的详细信息。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)