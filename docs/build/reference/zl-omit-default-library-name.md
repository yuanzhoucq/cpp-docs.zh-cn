---
title: /Zl（省略默认库名）
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: cb8083d874abe17add1d27096ebce143d03a04cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315542"
---
# <a name="zl-omit-default-library-name"></a>/Zl（省略默认库名）

省略.obj 文件中的默认 C 运行时库名称。 默认情况下，编译器将库的名称放入 .obj 文件中以将链接器定向到正确的库。

## <a name="syntax"></a>语法

```
/Zl
```

## <a name="remarks"></a>备注

默认库的详细信息，请参阅[使用运行时库](md-mt-ld-use-run-time-library.md)。

可以使用 **/Zl**你打算将放入一个库的.obj 文件进行编译。 虽然省略库名称节省仅少量空间来容纳单一.obj 文件，但保存的总空间至关重要，在包含许多对象模块库中。

此选项是一个高级的选项。 设置此选项移除可能所必需的应用程序，从而导致链接时错误，如果你的应用程序依赖于这种支持某些 C 运行时库支持。 如果使用此选项必须提供某种其他方式所需的组件。

使用[/NODEFAULTLIB （忽略库）](nodefaultlib-ignore-libraries.md)。 若要指示链接器忽略所有.obj 文件中的库引用。

有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。

使用编译时 **/Zl**，`_VC_NODEFAULTLIB`定义。  例如：

```
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

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**高级**属性页。

1. 修改**省略默认库名称**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
