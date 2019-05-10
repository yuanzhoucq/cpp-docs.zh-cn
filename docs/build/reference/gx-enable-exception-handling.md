---
title: /GX（启用异常处理）
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 43be8f6d0f080f0d85568ce5b089751fc68f0e8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291998"
---
# <a name="gx-enable-exception-handling"></a>/GX（启用异常处理）

已否决。 启用同步异常处理使用函数假设使用声明`extern "C"`永远不会引发异常。

## <a name="syntax"></a>语法

```
/GX
```

## <a name="remarks"></a>备注

**/GX**已弃用。 使用等效[/EHsc](eh-exception-handling-model.md)选项。 有关不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**主题中[按类别列出的编译器选项](compiler-options-listed-by-category.md)。

默认情况下 **/EHsc**，则等效于 **/GX**，实际上是通过使用 Visual Studio 开发环境编译时。 使用命令行工具时，指定的异常处理。 此命令的等效 **/GX-**。

有关详细信息，请参阅[C++的异常处理](../../cpp/cpp-exception-handling.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 在导航窗格中，选择**配置属性**， **C /C++**，**命令行**。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/EH（异常处理模型）](eh-exception-handling-model.md)
