---
title: cl.exe 的返回值
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 627d20a85b8f31ab881588533840a888334e9847
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373770"
---
# <a name="return-value-of-clexe"></a>cl.exe 的返回值

cl.exe 在成功（无错误）时返回零；否则返回非零值。

如果从脚本、powershell、.cmd 或 .bat 文件编译，则 cl.exe 的返回值很有用。 建议在出现错误或警告时捕获编译器的输出，以便能解决它们。

有太多可能的错误退出代码，cl.exe 无法将它们一一列出。 可以在% ProgramFiles （x86）% \ Windows 工具包 \\ <em>版本</em>\Include\shared\ 目录中包含的 Windows 软件开发工具包中的 winerror.h 或 ntstatus 文件中查找错误代码。 以十进制返回的错误代码必须转换为十六进制才能搜索。 例如，错误代码 -1073741620 转换为十六进制为 0xC00000CC。 在 ntstatus.h 中发现了此错误，对应的消息为“无法在远程服务器上找到指定共享名。” 有关 Windows 错误代码的可下载列表，请参阅[&#91;ERREF&#93;： Windows 错误代码](https://docs.microsoft.com/openspecs/windows_protocols/MS-ERREF)。

还可使用 Visual Studio 中的错误查找实用工具来了解编译器错误消息的意思。 在 Visual Studio 命令行界面中，输入**errlook.exe**以启动该实用工具;或在 Visual Studio IDE 中的菜单栏上，依次选择 "**工具**"、"**错误查找**"。 输入错误值以查找与错误相关的描述性文本。 有关详细信息，请参阅[ERRLOOK Reference](errlook-reference.md)。

## <a name="remarks"></a>备注

下面是一个使用 cl.exe 的返回值的示例 .bat 文件。

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>另请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
