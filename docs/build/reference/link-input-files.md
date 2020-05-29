---
title: LINK 输入文件
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328202"
---
# <a name="link-input-files"></a>LINK 输入文件

向链接器提供包含对象、导入和标准库、资源、模块定义和命令输入的文件。 LINK 不使用文件扩展名对文件内容进行假设。 相反，LINK 会检查每个输入文件，以确定该文件是哪一类文件。

命令行上的对象文件按照它们在命令行上显示的顺序进行处理。 库也按命令行顺序进行搜索，并带有以下警告：首先在库中搜索未解析的符号，然后从命令行和[/DEFAULTLIB（指定默认库）](defaultlib-specify-default-library.md)指令中搜索以下库，然后搜索命令行开头的任何库。

> [!NOTE]
> LINK 不再接受分号（或任何其他字符）作为响应文件和订单文件中注释的开头。 分号仅识别为模块定义文件 （.def） 中注释的开始。

LINK 使用以下类型的输入文件：

- [.obj 文件](dot-obj-files-as-linker-input.md)

- [.netmodule 文件](netmodule-files-as-linker-input.md)

- [.lib 文件](dot-lib-files-as-linker-input.md)

- [.exp 文件](dot-exp-files-as-linker-input.md)

- [.def 文件](dot-def-files-as-linker-input.md)

- [.pdb 文件](dot-pdb-files-as-linker-input.md)

- [.res 文件](dot-res-files-as-linker-input.md)

- [.exe 文件](dot-exe-files-as-linker-input.md)

- [.txt 文件](dot-txt-files-as-linker-input.md)

- [.ilk 文件](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
