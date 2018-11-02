---
title: /hotpatch（创建可热修补的映像）
ms.date: 11/04/2016
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: b304edffc024fac084338789134269745111ba00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581436"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch（创建可热修补的映像）

准备映像以进行热修补。

## <a name="syntax"></a>语法

```
/hotpatch
```

## <a name="remarks"></a>备注

当 **/hotpatch**使用在编译时，编译器可确保每个函数的第一个指令为至少两个字节，这是进行热修补所要求。

若要完成使用后使映像可以热修补，准备 **/hotpatch**进行编译，必须使用[/FUNCTIONPADMIN （创建可热修补映像）](../../build/reference/functionpadmin-create-hotpatchable-image.md)链接。 编译和链接映像使用的 cl.exe，一次调用时 **/hotpatch**意味着 **/functionpadmin**。

因为说明始终是两个字节或 ARM 体系结构，更大并且 x64 编译总是被视为如同 **/hotpatch**已指定，无需指定 **/hotpatch**时编译为这些目标;但是，你必须仍使用链接 **/functionpadmin**若要为其创建可热修补映像。 **/Hotpatch**编译器选项仅影响 x86 编译。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**C/c + +** 文件夹。

1. 选择**命令行**属性页。

1. 添加到编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="guidance"></a>指导

有关更新管理的详细信息，请参阅"安全指南的更新管理"在[ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx)。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)