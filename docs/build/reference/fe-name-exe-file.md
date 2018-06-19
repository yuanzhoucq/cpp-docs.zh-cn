---
title: -Fe （命名 EXE 文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fe
dev_langs:
- C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0afd8a863c9b8482e2b7f3868047845818bd2923
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377052"
---
# <a name="fe-name-exe-file"></a>/Fe（命名 EXE 文件）

指定名称和.exe 文件或 DLL 由编译器创建的目录。

## <a name="syntax"></a>语法

> **/Fe**[_pathname_]  
> **/ Fe:** _路径名_  

### <a name="arguments"></a>自变量

*路径名*<br/>
相对或绝对路径和基文件名或到目录或要用于生成可执行文件的基文件名称的相对或绝对路径。

## <a name="remarks"></a>备注

**/Fe**选项允许你指定的输出目录、 输出可执行文件名称，或同时包括这两者，生成的可执行文件。 如果*路径名*路径分隔符中结束 (**&#92;**)，则假定它仅指定输出目录。 否则为最后一个组件的*路径名*用作输出文件基名称和的其余部分*路径名*指定的输出目录。 如果*路径名*不具有任何路径分隔符，则假定它在当前目录中指定输出文件的名称。 *路径名*必须括在双引号 (**"**) 如果它包含不能在一个短的路径，例如空间，任何字符扩展字符或路径组件数量超过八个字符长时间。

当 **/Fe**未指定选项，或如果基文件中未指定名称*路径名*，编译器中赋予输出文件的默认名称，使用指定的第一个源或对象文件的基名称在命令行和扩展名为.exe 或.dll。

如果指定[（编译而无需链接） 的 /c](c-compile-without-linking.md)选项， **/Fe**不起作用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 打开**配置属性** > **链接器** > **常规**属性页。

1. 修改**输出文件**属性。 选择**确定**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。

## <a name="example"></a>示例

下面的命令行编译并链接当前目录中的所有 C 源文件。 生成的可执行文件被命名为 PROCESS.exe 和的目录"C:\Users\User Name\repos\My Project\bin"中创建。

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>示例

下面的命令行创建中的可执行文件`C:\BIN`具有相同基名称为当前目录中的第一个源文件：

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)<br/>
