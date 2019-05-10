---
title: /BASE（基址）
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
ms.openlocfilehash: dc6380903af0be2e6696ca3589813c249f71dd05
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812273"
---
# <a name="base-base-address"></a>/BASE（基址）

指定的程序的基址。

## <a name="syntax"></a>语法

> **/BASE:**{*address*[**,**<em>size</em>] | **\@**<em>filename</em>**,**<em>key</em>}

## <a name="remarks"></a>备注

> [!NOTE]
> 出于安全原因，Microsoft 建议你使用[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)选项而不是指定可执行文件的基址。 这会生成可以随机变基可在加载时使用地址空间布局随机化 (ASLR) 功能的 Windows 可执行映像。 /DYNAMICBASE 选项在默认情况下处于打开状态。

/ 基数选项设置为该程序，重写的默认位置为.exe 或 DLL 文件的基址。 .Exe 文件的默认基址是为 32 位映像 0x400000 处或 0x140000000 为 64 位映像。 对于 DLL 的默认基址是为 32 位映像 0x10000000 或 0x180000000 为 64 位映像。 在操作系统上不支持地址空间布局随机化 (ASLR)，或设置 /dynamicbase: no 选项时，操作系统首次尝试加载程序在其指定或默认基址。 如果有足够的空间有不可用，系统重新定位到该程序。 若要防止重定位，请使用[/fixed](fixed-fixed-base-address.md)选项。

如果链接器将发出错误*地址*不是 64 K 的倍数。 您可以选择指定程序; 的大小如果程序不适合在您指定的大小将链接器发出警告。

在命令行中，指定的基址另一种方法是使用基址响应文件。 基址响应文件是文本文件，其中包含的基址和可选大小将使用您的程序，所有 Dll 和每个基址的唯一文本键。 若要通过使用响应文件指定基址，使用 at 符号 (**\@**) 的响应文件的名称后跟*filename*后, 跟一个逗号，则*密钥*文件中使用的基址的值。 链接器寻找*文件名*中指定的路径或如果未指定路径，LIB 环境变量中指定的目录中。 中的每一行*文件名*表示一个 DLL 并具有以下语法：

> *键* *地址*[*大小*] **;** *注释*

*密钥*是字母数字字符的字符串，不区分大小写。 它通常是 DLL 的名称，但它不需要。 *键*跟基*地址*中 C 语言、 十六进制或十进制表示法和可选的最大*大小*。 所有三个参数由空格或制表符分隔。 链接器将发出警告，如果指定*大小*小于程序所需的虚拟地址空间。 一个*注释*指定由分号 (**;**) 并且可在相同或在单独的行。 链接器将忽略从分号到行尾的所有文本。 此示例显示了此类文件的一部分：

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

如果包含这些行的文件为 dlls.txt，下面的示例命令将应用此信息：

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

若要设置的基址的另一种方法是使用*基*中的参数[名称](name-c-cpp.md)或[库](library.md)语句。 /BASE 和[/DLL](dll-build-a-dll.md)选项一起构成了等效于**库**语句。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **高级**属性页。

1. 修改**基址**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
