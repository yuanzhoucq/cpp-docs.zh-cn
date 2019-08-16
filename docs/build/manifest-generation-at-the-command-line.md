---
title: 命令行上的清单生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493195"
---
# <a name="manifest-generation-at-the-command-line"></a>命令行上的清单生成

当使用 nmake 或C++类似的工具从命令行生成 C/应用程序时, 会在链接器处理完所有对象文件并生成最终的二进制文件后生成清单。 链接器收集存储在对象文件中的程序集信息, 并将此信息合并到最终清单文件中。 默认情况下, 链接器将生成一个名为*binary_name*的文件。用于描述最终二进制文件的*扩展名*。 链接器不会将清单文件嵌入到二进制文件中, 并且只能生成一个清单作为外部文件。 有多种方法可以将清单嵌入到最终二进制文件中, 如使用[清单工具 (mt.exe)](/windows/win32/sbscs/mt-exe)或将清单编译到资源文件中。 请务必记住, 在最终二进制文件中嵌入清单时必须遵循特定的规则, 以启用增量链接、签名和编辑并继续等功能。 以下内容讨论[了这些选项和其他选项:在命令行上生成时,C++将](how-to-embed-a-manifest-inside-a-c-cpp-application.md)清单嵌入到 C/应用程序中。

## <a name="see-also"></a>请参阅

[进行](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL（增量链接）](reference/incremental-link-incrementally.md)<br/>
[强名称程序集（程序集签名）(C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[编辑并继续](/visualstudio/debugger/edit-and-continue)<br/>
[了解 C/C++ 程序的清单生成](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
