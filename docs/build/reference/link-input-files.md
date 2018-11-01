---
title: LINK 输入文件
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: a5aaf162a16b6989ac1abbcb6a574af1c31b543a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550548"
---
# <a name="link-input-files"></a>LINK 输入文件

链接器提供文件，其中包含的对象、 导入和标准库、 资源、 模块定义和输入的命令。 链接不使用文件扩展名进行假设文件的内容。 相反，链接将检查每个输入的文件以确定它是什么类型的文件。

命令行上出现的顺序处理命令行上的对象文件。 库中，命令行顺序搜索以下一点： 符号无法解析时将在库中的对象文件中搜索在该库中第一次，，，然后从命令行和以下库[/DEFAULTLIB （指定默认库）](../../build/reference/defaultlib-specify-default-library.md)指令，然后到命令行的开头的所有库。

> [!NOTE]
>  链接不再接受以分号 （或任何其他字符） 作为响应文件和顺序文件中注释的开始。 分号仅认为模块定义文件 (.def) 中的注释的开始。

链接使用以下类型的输入文件：

- [.obj 文件](../../build/reference/dot-obj-files-as-linker-input.md)

- [.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)

- [.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)

- [.exp 文件](../../build/reference/dot-exp-files-as-linker-input.md)

- [.def 文件](../../build/reference/dot-def-files-as-linker-input.md)

- [.pdb 文件](../../build/reference/dot-pdb-files-as-linker-input.md)

- [.res 文件](../../build/reference/dot-res-files-as-linker-input.md)

- [.exe 文件](../../build/reference/dot-exe-files-as-linker-input.md)

- [.txt 文件](../../build/reference/dot-txt-files-as-linker-input.md)

- [.ilk 文件](../../build/reference/dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)