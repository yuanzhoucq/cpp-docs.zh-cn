---
title: /Gy（启用函数级链接）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 368bd469a303222ef4d5177677de4940e402b6de
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413103"
---
# <a name="gy-enable-function-level-linking"></a>/Gy（启用函数级链接）

允许编译器以打包函数 (COMDAT) 形式对各个函数进行打包。

## <a name="syntax"></a>语法

```
/Gy[-]
```

## <a name="remarks"></a>备注

链接器需要函数进行单独打包为 Comdat 中排除或 DLL 或.exe 文件中的各个函数进行排序。

可以使用链接器选项[/OPT （优化）](../../build/reference/opt-optimizations.md)以从.exe 文件中排除未引用的封装的函数。

可以使用链接器选项[/ORDER （按顺序放置函数）](../../build/reference/order-put-functions-in-order.md)将封装的函数包括.exe 文件中指定的顺序。

如果实例化为调用内联函数则始终打包 (其中发生，例如，如果内联已关闭或采用函数地址)。 此外，自动打包在类声明中定义的 c + + 成员函数;其他函数是不是，并选择此选项所需将其编译为封装函数。

> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)选项，用于编辑并继续，将自动设置 **/Gy**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**代码生成**属性页。

1. 修改**启用函数级链接**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
