---
title: /GA（Windows 应用程序优化）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: bd6c4a3464762a24c9079bb79318ad3b0f05b74a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420708"
---
# <a name="ga-optimize-for-windows-application"></a>/GA（Windows 应用程序优化）

中的.exe 文件的访问线程本地存储 (TLS) 的变量更高效的代码的结果。

## <a name="syntax"></a>语法

```
/GA
```

## <a name="remarks"></a>备注

**/GA**对数据的速度访问使用声明[__declspec （thread)](../../cpp/declspec.md)在基于 Windows 的程序中。 设置此选项， [__tls_index](/windows/desktop/ProcThread/thread-local-storage)宏被假定为 0。

使用 **/GA**为 DLL 可能会导致代码生成错误。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
