---
title: "-O 选项 （优化代码） |Microsoft 文档"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7da04384d0c4ea00c2eaaedbcf0ec770e216289
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="o-options-optimize-code"></a>/O 选项（优化代码）

**/O**选项控制各种优化，可帮助你创建具有最大速度或最小大小代码。

- [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)设置的组合生成最小大小代码优化。

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)设置优化的组合，用于优化代码的最大速度。

- [/Ob](../../build/reference/ob-inline-function-expansion.md)控制内联函数展开。

- [/Od](../../build/reference/od-disable-debug.md)禁用优化，以便加快编译并简化调试。

- [/Og](../../build/reference/og-global-optimizations.md)启用全局优化。

- [/Oi](../../build/reference/oi-generate-intrinsic-functions.md)为适当的函数调用生成内部函数。

- [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)告知编译器优选速度的优化大小。

- [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) （默认设置） 将告知编译器优选大小优化的速度。

- [/Ox](../../build/reference/ox-full-optimization.md)是一种组合选项，选择多个主要侧重于速度的优化。 它是的严格子集**/O2**优化。

- [/Oy](../../build/reference/oy-frame-pointer-omission.md)取消的速度更快的函数调用的调用堆栈上的帧指针的创建。

## <a name="remarks"></a>备注

你可以组合多个**/O**到单个选项语句的选项。 例如， **/Odi**相同**/Od /Oi**。 某些选项相互排斥，导致编译器错误，如果将一起使用。 请参阅个人**/O**有关详细信息的选项。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)   
[设置编译器选项](../../build/reference/setting-compiler-options.md)