---
title: /vmb、-vmg （表示方法）
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: eac41de04ec883e7b5acf26596647f912b0b1d20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808477"
---
# <a name="vmb-vmg-representation-method"></a>/vmb、/vmg（表示方法）

选择编译器用来表示对类成员的指针的方法。

使用 **/vmb**如果始终在声明类的成员的指针之前定义一个类。

使用 **/vmg**来定义类之前声明指向类的成员。 如果在相互引用的两个不同的类中定义成员，可能会发生这种需求。 对于这种相互引用的类，首先定义必须引用一个类。

## <a name="syntax"></a>语法

```
/vmb
/vmg
```

## <a name="remarks"></a>备注

此外可以使用[pointers_to_members](../../preprocessor/pointers-to-members.md)或[继承关键字](../../cpp/inheritance-keywords.md)代码中用于指定指针表示形式。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
