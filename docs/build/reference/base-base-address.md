---
title: 基于 （基址） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4090a3e8d2f9f3bdcb68875d94a1b84e7bff0f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376619"
---
# <a name="base-base-address"></a>/BASE（基址）
```  
/BASE:{address[,size] | @filename,key}  
```  
  
 / BASE 选项设置重写的.exe 或 DLL 文件的默认位置，该程序的基址。 .Exe 文件的默认基址是为 32 位映像 0x400000 或 0x140000000 为 64 位映像。 对于 DLL，默认基址是为 32 位映像 0x10000000 或 0x180000000 为 64 位映像。 在操作系统上不支持地址空间布局随机化 (ASLR) 或 /DYNAMICBASE:NO 选项已设置时，操作系统首先尝试加载程序在其指定或默认基址。 如果足够的空间存在不可用，系统将重新定位该程序。 若要防止重定位，请使用[/固定](../../build/reference/fixed-fixed-base-address.md)选项。  
  
 如果链接器会发出错误*地址*不是 64k 的倍数。 你可以选择指定程序; 的大小如果程序不能放在你指定的大小，则链接器将发出警告。  
  
 在命令行中，另一种方法指定的基址是通过使用基址响应文件。 基址响应文件是包含基址和可选大小将使用你的程序的所有 Dll 和每个基址的唯一文本键的文本文件。 若要通过使用响应文件指定一个基址，使用 at 符号 (@) 的响应文件的名称后跟*filename*后, 跟一个逗号，则`key`在文件中使用的基址的值。 链接器查找*filename*中指定的路径或如果未指定路径，在 LIB 环境变量中指定的目录中。 中的每一行*filename*表示一个 DLL，并具有以下语法：  
  
```  
  
key address [size] ;comment  
```  
  
 `key`是字母数字字符的字符串和不区分大小写。 它通常是 DLL 的名称，但它不需要。 `key`后跟一个基*地址*中 C 语言、 十六进制或十进制表示法和可选的最大`size`。 所有三个自变量由空格或制表符分隔。 链接器将发出警告，如果指定`size`小于所需的程序的虚拟地址空间。 A`comment`指定由分号 （;），并且可以是在相同或单独的行上。 链接器将忽略所有从分号至行尾的文本。 此示例演示此类文件的一部分：  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 如果包含以下行的文件为 dlls.txt，下面的示例命令将应用此信息：  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## <a name="remarks"></a>备注  
 出于安全原因，Microsoft 建议你使用[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)而不是指定基址的可执行文件的选项。 这将生成可执行映像可以是随机重新设定基址在加载时使用地址空间布局随机化 (ASLR) 功能的 Windows。 默认情况下，/DYNAMICBASE 选项处于启用状态。  
  
 另一种方法中设置基址是使用*基*中的参数[名称](../../build/reference/name-c-cpp.md)或[库](../../build/reference/library.md)语句。 /BASE 和[/DLL](../../build/reference/dll-build-a-dll.md)选项一起构成了等效于**库**语句。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**链接器**文件夹。  
  
3.  选择**高级**属性页。  
  
4.  修改**基址**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)