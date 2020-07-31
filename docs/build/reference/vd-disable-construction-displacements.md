---
title: /vd（禁用构造置换）
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: df8891cc71dd5a4cfd417969578c0c1b46ae3be3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223806"
---
# <a name="vd-disable-construction-displacements"></a>/vd（禁用构造置换）

## <a name="syntax"></a>语法

```
/vdn
```

## <a name="arguments"></a>参数

**0**<br/>
禁止 vtordisp 构造函数/析构函数置换成员。 仅当你确定所有类构造函数和析构函数都确实调用虚函数时，才选择此选项。

**1**<br/>
启用隐藏 vtordisp 构造函数/析构函数置换成员的创建。 此选项为默认选项。

**2**<br/>
允许对正在构造的对象使用[Dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)。 例如，从虚拟基类到派生类的 dynamic_cast。

当具有虚拟函数的虚拟基时， **/vd2**会添加 vtordisp 字段。 **/vd1**应该足以满足需要。 最常见的情况是， **/vd2**的唯一虚拟函数是一个析构函数。

## <a name="remarks"></a>备注

这些选项仅适用于使用虚拟基的 c + + 代码。

Visual C++ 在使用虚拟继承的情况下实现 c + + 构造置换支持。 构造置换解决了在构造更进一步的派生类的过程中，当在派生类中声明并在派生类中重写的虚函数时，创建的问题。

问题在于，可能会向虚拟函数传递错误的 **`this`** 指针，这是因为对类的虚拟基进行了置换和对其派生类的置换。 解决方案为类的每个虚拟基提供单个构造置换调整（称为 vtordisp 字段）。

默认情况下，只要代码定义用户定义的构造函数和析构函数，并且还会重写虚拟基的虚函数，就会引入 vtordisp 字段。

这些选项会影响整个源文件。 使用[vtordisp](../../preprocessor/vtordisp.md)逐个类地取消和重新启用 vtordisp 字段。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行” **** 属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
