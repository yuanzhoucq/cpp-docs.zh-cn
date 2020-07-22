---
title: /GT（支持纤程安全的线程本地存储区）
description: MSVC 编译器选项/GT 对线程本地存储数据启用安全优化。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 1b1d9f6514cec8c3d247f86be063f2ac3e0dfe72
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180807"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>`/GT` (支持纤程安全的线程本地存储) 

支持使用静态线程本地存储分配的数据的纤程安全，即用分配的数据 `__declspec(thread)` 。

## <a name="syntax"></a>语法

> **`/GT`**

## <a name="remarks"></a>备注

使用声明的数据 `__declspec(thread)` 通过线程本地存储 (TLS) 阵列进行引用。 TLS 数组是系统为每个线程维护的地址的数组。 此数组中的每个地址提供线程本地存储数据的位置。

纤程是一种轻量对象，它由一个堆栈和一个寄存器上下文组成，可以在不同的线程上计划。 纤程可以在任何线程上运行。 由于纤程可能会在其他线程上换出并重新启动，因此编译器不得缓存 TLS 数组的地址，或将其作为公共子表达式通过函数调用进行优化。 **`/GT`** 禁止这种优化。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **优化**" 属性页。

1. 修改 "**启用纤程安全优化**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
