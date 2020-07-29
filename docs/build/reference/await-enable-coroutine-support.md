---
title: /await（启用协同程序支持）
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: 526216ba2ae259b53bcf77691ebd09a6152b83f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223923"
---
# <a name="await-enable-coroutine-support"></a>/await（启用协同程序支持）

使用 **/await**编译器选项可为协同程序启用编译器支持。

## <a name="syntax"></a>语法

> /await

## <a name="remarks"></a>备注

**/Await**编译器选项支持 c + + 协同程序和关键字、和的编译器支持 **`co_await`** **`co_yield`** **`co_return`** 。 默认情况下，此选项处于关闭状态。 有关 Visual Studio 中的协同程序支持的信息，请参阅[Visual Studio 团队博客](https://devblogs.microsoft.com/cppblog/category/coroutine/)。 有关协同程序标准方案的详细信息，请参阅[N4628 工作草案：协同程序的 c + + 扩展技术规范](https://wg21.link/n4628)。

从 Visual Studio 2015 开始，可以使用 **/await**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的 "**属性页**" 对话框。

1. 在 "**配置属性**" 下，展开 " **c/c + +** " 文件夹，然后选择 "**命令行**" 属性页。

1. 在 "**附加选项**" 框中输入 **/await**编译器选项。 选择 **"确定" 或 "** **应用**" 保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
