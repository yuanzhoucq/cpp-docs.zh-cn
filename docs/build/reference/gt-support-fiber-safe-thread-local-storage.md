---
title: /GT（支持纤程安全的线程本地存储区）
ms.date: 11/04/2016
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
ms.openlocfilehash: 417ac00a446f773a424553e42478a4f0cf58efc6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822511"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT（支持纤程安全的线程本地存储区）

分配使用静态线程本地存储区，即使用分配的数据的数据支持纤程安全`__declspec(thread)`。

## <a name="syntax"></a>语法

```
/GT
```

## <a name="remarks"></a>备注

使用声明数据`__declspec(thread)`通过线程本地存储 (TLS) 数组引用。 TLS 数组是系统会为每个线程维护的地址的数组。 此数组中的每个地址提供的线程本地存储的数据的位置。

纤程是轻型对象，堆栈和寄存器上下文组成，并可以在各种线程上安排。 纤程可以在任何线程上运行。 纤程可能会被置换出和更高版本上重新启动另一个线程，因为 TLS 数组的地址不得缓存或作为公共子表达式优化整个函数调用 (请参阅[/Og （全局优化）](og-global-optimizations.md)选项详细信息）。 **/GT**可防止这种优化。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**优化**属性页。

1. 修改**启用纤程安全优化**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
