---
title: /Zp（结构成员对齐）
ms.date: 04/04/2019
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
ms.openlocfilehash: d76cd93c7af4228bff8f73fa3bcbf40fa149b0be
ms.sourcegitcommit: 35c4b3478f8cc310ebbd932a18963ad8ab846ed9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59237159"
---
# <a name="zp-struct-member-alignment"></a>/Zp（结构成员对齐）

控制结构的成员的打包到内存的方式，并在模块中指定的所有结构相同的封装。

## <a name="syntax"></a>语法

> **/Zp**[**1**|**2**|**4**|**8**|**16**]

## <a name="remarks"></a>备注

**/Zp**_n_选项告知编译器存储每个结构成员的位置。 编译器存储之后的是较小的一个成员类型的大小的边界上的第一个成员或*n*-字节边界。

下表中列出了该可用装箱值：

|/Zp 参数|效果|
|-|-|
|1|针对 1 字节边界将结构打包。 与相同 **/Zp**。|
|2|针对 2 字节边界将结构打包。|
|4|针对 4 字节边界将结构打包。|
|8|针对 8 字节边界 （x86、 ARM 和 ARM64 的默认值） 将结构打包。|
|16| 针对 16 字节边界 （默认值适用于 x64） 将结构打包。|

不要使用此选项，除非有特定的对齐要求。

> [!WARNING]
> Windows SDK 中的 c + + 标头设置和假设 **/zp8**打包在内部。 如果可能发生损坏的内存 **/Zp** Windows SDK 标头内更改设置。 标头，不会影响任何 **/Zp**命令行设置的选项。

此外可以使用[pack](../../preprocessor/pack.md)控制结构封装。 有关对齐的详细信息，请参阅：

- [align](../../cpp/align-cpp.md)

- [__alignof 运算符](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [/ALIGN（节对齐）](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **代码生成**属性页。

1. 修改**结构成员对齐**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md) \
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
