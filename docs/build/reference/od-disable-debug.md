---
title: /Od（禁用（调试））
ms.date: 11/04/2016
f1_keywords:
- /od
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
ms.openlocfilehash: 386113c7926085aa7e82e23768556372014a8cc8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426246"
---
# <a name="od-disable-debug"></a>/Od（禁用（调试））

关闭该程序中的所有优化并加快编译。

## <a name="syntax"></a>语法

```
/Od
```

## <a name="remarks"></a>备注

此选项默认值。 因为 **/Od**取消代码移动，所以简化调试过程。 有关编译器选项进行调试的详细信息，请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**优化**属性页。

1. 修改**优化**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/Z7、/Zi、/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)
