---
title: /await （启用协同程序支持）
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: c0c8c0183c356900ba8f95d39e427d56eb1ec96b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294993"
---
# <a name="await-enable-coroutine-support"></a>/await （启用协同程序支持）

使用 **/await**编译器选项来启用协同程序的编译器支持。

## <a name="syntax"></a>语法

> /await

## <a name="remarks"></a>备注

**/Await**编译器选项让编译器对支持C++协同例程和关键字**co_await**， **co_yield**，并**co_return**. 默认情况下，此选项处于关闭状态。 在 Visual Studio 中的协同例程支持有关的信息，请参阅[Visual Studio 团队博客](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/)。 有关协同例程标准建议的详细信息，请参阅[N4628 工作草案、 技术规范C++扩展协同例程](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf)。

**/Await**选项是在 Visual Studio 2015 开始提供。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开你的项目**属性页**对话框。

1. 下**配置属性**，展开**C /C++** 文件夹，然后选择**命令行**属性页。

1. 输入 **/await**中的编译器选项**其他选项**框。 选择**确定**或**应用**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
