---
title: /Zl（省略默认库名）
ms.date: 11/04/2016
f1_keywords:
- /zl
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: c72377314abf755469075c7a4b431f4b8a64ee7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438632"
---
# <a name="zl-omit-default-library-name"></a>/Zl（省略默认库名）

省略 .obj 文件中的默认 C 运行时库名称。 默认情况下，编译器将库的名称放入 .obj 文件中以将链接器定向到正确的库。

## <a name="syntax"></a>语法

```
/Zl
```

## <a name="remarks"></a>备注

有关默认库的详细信息，请参阅[使用运行时库](md-mt-ld-use-run-time-library.md)。

你可以使用 **/zl**来编译你计划放入库中的 .obj 文件。 尽管省略了库名称只为单个 .obj 文件保存了少量空间，但在包含多个对象模块的库中保存的总空间非常重要。

此选项是一个高级选项。 如果设置此选项，则将删除您的应用程序可能需要的某些 C 运行时库支持，如果您的应用程序依赖于此支持，则会导致链接时错误。 如果使用此选项，则必须以其他方式提供所需的组件。

使用[/NODEFAULTLIB （忽略库）](nodefaultlib-ignore-libraries.md)。 指示链接器忽略所有 .obj 文件中的库引用。

有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。

用 **/zl**编译时，将定义 `_VC_NODEFAULTLIB`。  例如：

```cpp
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击 "**高级**" 属性页。

1. 修改 "**省略默认库名称**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
