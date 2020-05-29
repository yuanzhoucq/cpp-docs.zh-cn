---
title: /Fe（命名 EXE 文件）
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: f0bd8f3a96555cc29d06f74fb44a73bbed32889b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825573"
---
# <a name="fe-name-exe-file"></a>/Fe（命名 EXE 文件）

指定由编译器创建的 .exe 文件或 DLL 的名称和目录。

## <a name="syntax"></a>语法

> **/Fe**[_pathname_] \
> **/Fe：** _pathname_

### <a name="arguments"></a>参数

*路径名*<br/>
相对或绝对路径和基文件名称，或目录的相对或绝对路径，或者要用于生成的可执行文件的基文件名。

## <a name="remarks"></a>备注

通过 **/Fe**选项，可以指定生成的可执行文件的输出目录、输出可执行文件名称或同时指定两者。 如果*路径名*以路径分隔符（**&#92;**）结尾，则假定它仅指定输出目录。 否则， *pathname*的最后一个部分将用作输出文件基名称，其余的*pathname*指定输出目录。 如果*路径名*没有任何路径分隔符，则假定指定当前目录中的输出文件名。 如果路径包含的字符不能在短路径中（如空格、扩展字符或路径部分的长度超过8个字符），则必须将*路径名*括在双引号（**"**）中。

如果未指定 **/Fe**选项，或未在*pathname*中指定文件基名称，编译器将使用命令行上指定的第一个源或对象文件的基名称和扩展名 .exe 或 .dll 为输出文件指定默认名称。

如果指定[/c （Compile 但不链接）](c-compile-without-linking.md)选项，则 **/Fe**不起作用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开**配置属性** > **链接器** > **常规**属性页。

1. 修改 "**输出文件**" 属性。 选择“确定”以保存更改****。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A> 。

## <a name="example"></a>示例

以下命令行编译和链接当前目录中的所有 C 源文件。 生成的可执行文件命名为 store.exe，并在目录 "C:\users\ 用户名 Name\repos\My Project\bin" 中创建。

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>示例

以下命令行在中`C:\BIN`创建一个可执行文件，该文件与当前目录中的第一个源文件具有相同的基名称：

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>另请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)<br/>
