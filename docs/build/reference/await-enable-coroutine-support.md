---
title: -await （启用协同程序支持） |Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09cab9f0c7d94c3c51eb63008ec6b7cfb1292f89
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860571"
---
# <a name="await-enable-coroutine-support"></a>/await （启用协同程序支持）

使用 **/await**编译器选项来启用协同程序的编译器支持。

## <a name="syntax"></a>语法

> /await

## <a name="remarks"></a>备注

**/Await**编译器选项让编译器对 c + + 协同例程和关键字支持**co_await**， **co_yield**，和**co_return**. 默认情况下，此选项处于关闭状态。 在 Visual Studio 中的协同例程支持有关的信息，请参阅[Visual Studio 团队博客](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/)。 有关协同例程标准建议的详细信息，请参阅[N4628 工作草案，协同例程的 c + + 扩展的技术规范](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf)。

**/Await**选项是在 Visual Studio 2015 开始提供。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开你的项目**属性页**对话框。

1. 下**配置属性**，展开**C/c + +** 文件夹，然后选择**命令行**属性页。

1. 输入 **/await**中的编译器选项**其他选项**框。 选择**确定**或**应用**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
