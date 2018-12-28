---
title: /Zp（结构成员对齐）
ms.date: 12/17/2018
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: d1821d8dc5eab202a918893a1e7895151629b551
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627522"
---
# <a name="zp-struct-member-alignment"></a>/Zp（结构成员对齐）

控制结构的成员的打包到内存的方式，并在模块中指定的所有结构相同的封装。

## <a name="syntax"></a>语法

> **/Zp**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>备注

当指定 **/Zp**_n_选项，每个结构成员后第一个存储在成员类型的大小或*n*-字节边界 (其中*n*是 1、 2、 4、 8 或 16)，两者中较小。

下表中列出了该可用装箱值：

|/Zp 参数|效果|
|-|-|
|1|针对 1 字节边界将结构打包。 与相同 **/Zp**。|
|2|针对 2 字节边界将结构打包。|
|4|针对 4 字节边界将结构打包。|
|8|针对 8 字节边界 （默认值） 将结构打包。|
|16| 针对 16 字节边界将结构打包。|

除非有特定的对齐要求，不应使用此选项。

> [!WARNING]
> Windows SDK 中的 c + + 标头假定 **/zp8**打包。 如果可能发生损坏的内存 **/Zp**使用 Windows SDK 标头时更改设置。

此外可以使用[pack](../../preprocessor/pack.md)控制结构封装。 有关对齐的详细信息，请参阅：

- [align](../../cpp/align-cpp.md)

- [__alignof 运算符](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [结构对齐示例](../../build/x64-software-conventions.md#examples-of-structure-alignment)(特定于 x64)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**C/c + +** > **代码生成**属性页。

1. 修改**结构成员对齐**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。

## <a name="see-also"></a>请参阅

- [编译器选项](../../build/reference/compiler-options.md)
- [设置编译器选项](../../build/reference/setting-compiler-options.md)
