---
title: CL 文件名语法
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: 1135e5c682b79fec5de808b61c93d370f05a3aa9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440236"
---
# <a name="cl-filename-syntax"></a>CL 文件名语法

CL 接受具有遵循 FAT、HPFS 或 NTFS 命名约定的名称的文件。 任何文件名均可以包含完整或部分路径。 完整路径包括驱动器名和一个或多个目录名。 CL 接受用反斜杠（\\）或正斜杠（/）分隔的文件名。 包含空格文件名必须用双引号字符引起来。 部分路径忽略 CL 假定为当前驱动器的驱动器名。 如果不指定路径，则 CL 假定该文件位于当前目录。

文件扩展名确定处理文件的方式。 已编译具有扩展名 .c、.cxx 或 .cpp 的 C 和 C++ 文件。 将其他文件（包括 .obj 文件、库 (.lib) 和模块定义 (.def) 文件）传递给链接器而无需处理。

## <a name="see-also"></a>另请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
