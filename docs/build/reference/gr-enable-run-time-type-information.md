---
title: /GR（启用运行时类型信息）
ms.date: 11/04/2016
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: 15ad453b10fd31de97bbc25f8062e628129076f5
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820596"
---
# <a name="gr-enable-run-time-type-information"></a>/GR（启用运行时类型信息）

添加代码以在运行时检查对象类型。

## <a name="syntax"></a>语法

```
/GR[-]
```

## <a name="remarks"></a>备注

当 **/GR**为 on 时，编译器会定义`_CPPRTTI`预处理器宏。 默认情况下 **/GR**上。 **/GR-** 禁用运行时类型信息。

使用 **/GR**如果编译器无法以静态方式解决在代码中的对象类型。 通常需要 **/GR**选项时你的代码使用[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)或[typeid](../../cpp/typeid-operator.md)。 但是， **/GR**会增加你的映像.rdata 节的大小。 如果你的代码不使用**dynamic_cast**或**typeid**， **/GR-** 可能会产生较小的图像。

有关运行时类型检查的详细信息，请参阅[运行时类型信息](../../cpp/run-time-type-information.md)中*c + + 语言参考*。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**语言**属性页。

1. 修改**启用运行时类型信息**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
