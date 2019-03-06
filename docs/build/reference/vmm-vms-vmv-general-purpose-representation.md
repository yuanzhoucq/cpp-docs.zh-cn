---
title: /vmm、-vms、-vmv （通用表示形式）
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 3c11572880a0b58a1ba82f2e794c9dbfbd521c44
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425206"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm、/vms、/vmv（通用表示形式）

使用何时[/vmb、 /vmg （表示方法）](../../build/reference/vmb-vmg-representation-method.md)选为[表示方法](../../build/reference/vmb-vmg-representation-method.md)。 这些选项指示尚未遇到类定义的继承模型。

## <a name="syntax"></a>语法

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>备注

下表描述了这些选项。

|选项|描述|
|------------|-----------------|
|**/vmm**|指定指向为另一个使用多个继承的类成员的指针的最常规的表示形式。<br /><br /> 在相应[继承关键字](../../cpp/inheritance-keywords.md)和参数[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)是**多继承关系**。<br /><br /> 这种表示形式大于所需的单一继承。<br /><br /> 如果类定义为其声明指向成员的继承模型是虚拟的编译器将生成错误。|
|**/vms**|指定指向为另一个使用没有继承或单一继承的类成员的指针的最常规的表示形式。<br /><br /> 在相应[继承关键字](../../cpp/inheritance-keywords.md)和参数[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)是**单继承**。<br /><br /> 这是指针的指向类的成员的最小可能表示形式。<br /><br /> 如果类定义为其声明指向成员的继承模型为多个或虚拟的编译器将生成错误。|
|**/vmv**|指定指向为另一个使用虚拟继承的类成员的指针的最常规的表示形式。 它永远不会导致错误，并且是默认值。<br /><br /> 在相应[继承关键字](../../cpp/inheritance-keywords.md)和参数[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)是**virtual_inheritance**。<br /><br /> 此选项需要更大的指针和额外的代码比其他选项的指针进行解释。|

当您指定这些继承模型选项之一时，该模型用于所有指向类成员，而不考虑它们的继承类型或指针是否声明之前或之后类。 因此，如果始终使用单一继承类时，您可以减少代码大小由使用进行编译 **/vms**; 但是，如果你想要使用最常见的情况 （但代价是最大的数据表示形式），编译与 **/vmv**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/vmb、/vmg（表示方法）](../../build/reference/vmb-vmg-representation-method.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
