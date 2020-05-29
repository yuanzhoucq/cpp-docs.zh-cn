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
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328278"
---
# <a name="gy-enable-function-level-linking"></a>/Gy（启用函数级链接）

允许编译器以打包函数 (COMDAT) 形式对各个函数进行打包。

## <a name="syntax"></a>语法

```
/Gy[-]
```

## <a name="remarks"></a>备注

链接器要求将函数单独打包为 COMDAT，以排除 DLL 或 .exe 文件中的各个函数或排序各个函数。

您可以使用链接器选项[/OPT（优化）](opt-optimizations.md)从 .exe 文件中排除未引用的打包函数。

您可以使用链接器选项[/ORDER（按顺序排列函数）](order-put-functions-in-order.md)在 .exe 文件中按指定顺序包含打包函数。

如果内联函数被实例化为调用（例如，如果内联已关闭或您获取函数地址），则始终打包它们。 此外，C++类声明中定义的成员函数将自动打包;其他函数不是，选择此选项是将它们编译为打包函数所必需的。

> [!NOTE]
> 用于编辑和继续的[/ZI](z7-zi-zi-debug-information-format.md)选项会自动设置 **/Gy**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击 **"代码生成"** 属性页。

1. 修改**启用函数级链接**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
