---
title: -vd （禁用构造置换） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vd
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e36607d362ded227199d0e12770715c52384a26
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700877"
---
# <a name="vd-disable-construction-displacements"></a>/vd（禁用构造置换）

## <a name="syntax"></a>语法

```
/vdn
```

## <a name="arguments"></a>自变量

**0**<br/>
禁止显示 vtordisp 构造函数/析构函数置换成员。 选择此选项仅当你确信所有类构造函数和析构函数都调用虚拟函数几乎。

**1**<br/>
启用隐藏的 vtordisp 构造函数/析构函数置换成员的创建。 选择此选项默认值。

**2**<br/>
可以使用[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)上正在构造的对象。 例如，从虚拟基类到派生类的 dynamic_cast。

**/ vd2**将 vtordisp 字段添加具有虚拟基具有虚函数时。 **/ vd1**应该是够用的。 最常见的情况 **/vd2**必须是虚拟基中唯一的虚拟函数是析构函数。

## <a name="remarks"></a>备注

这些选项仅适用于使用虚拟基的 c + + 代码。

Visual c + + 中使用虚拟继承的情况下实现 c + + 构造置换支持。 构造置换解决问题创建的虚函数，在虚拟基中声明，派生类中重写时，在进一步的派生类的构造过程中从构造函数调用。

问题在于，可能会不正确传递虚拟函数`this`指针作为结果的到虚拟置换之间的差异的基的类和派生类的位移。 该解决方案提供了为每个虚拟基的类调用的 vtordisp 字段中，单个构造置换调整。

默认情况下，代码定义了用户定义的构造函数和析构函数，并且还将重写虚函数的虚拟基时引入 vtordisp 字段。

这些选项会影响整个源文件。 使用[vtordisp](../../preprocessor/vtordisp.md)禁止显示，然后重新启用 vtordisp 字段基于类的类。

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