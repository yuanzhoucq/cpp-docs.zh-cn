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
ms.openlocfilehash: 53a6cf4b3d14ee97a324fa01f83c0d0fee61180b
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373692"
---
# <a name="await-enable-coroutine-support"></a>/await（启用协同程序支持）

使用 **/await**编译器选项可为协同程序启用编译器支持。

## <a name="syntax"></a>语法

> /await

## <a name="remarks"></a>备注

**/Await**编译器选项支持 c + + 的编译器支持、co_yield **co_await**、 **co_yield**和**co_return**。 默认情况下，此选项处于关闭状态。 有关 Visual Studio 中的协同程序支持的信息，请参阅[Visual Studio 团队博客](https://devblogs.microsoft.com/cppblog/category/coroutine/)。 有关协同程序标准方案的详细信息，请参阅[N4628 工作草案：协同程序的 c + + 扩展技术规范](https://wg21.link/n4628)。

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
