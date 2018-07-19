---
title: 编译器命令行语法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825121a111d47de6b012aad444907363ad8c2a36
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370116"
---
# <a name="compiler-command-line-syntax"></a>编译器命令行语法
CL 命令行使用以下语法：  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 下表介绍 CL 命令的输入。  
  
|条目|含义|  
|-----------|-------------|  
|*选项*|一个或多个[CL 选项](../../build/reference/compiler-options.md)。 请注意，所有选项都应用于指定的源的所有文件。 由正斜杠 （/） 或短划线 （-） 指定选项。 如果一个选项所需自变量，该选项的说明文档是否选项和自变量之间允许有空格。 （除外 /HELP 选项） 的选项名称区分大小写。 请参阅[CL 选项的顺序](../../build/reference/order-of-cl-options.md)有关详细信息。|  
|`file`|一个或多个源代码文件、.obj 文件或库的名称。 CL 编译源文件，并将.obj 文件和库的名称传递给链接器。 请参阅[CL 文件名语法](../../build/reference/cl-filename-syntax.md)有关详细信息。|  
|*lib*|一个或多个库名称。 CL 将这些名称传递给链接器。|  
|*命令文件*|包含多个选项和文件名的文件。 请参阅[CL 命令文件](../../build/reference/cl-command-files.md)有关详细信息。|  
|*-opt 链接的*|一个或多个[链接器选项](../../build/reference/linker-options.md)。 CL 将这些选项传递给链接器。|  
  
 只要在命令行上的字符数不能超过 1024，由操作系统限制，可以指定任意数量的选项、 文件名和库名称。  
  
 Cl.exe 的返回值的信息，请参阅[cl.exe 的返回值](../../build/reference/return-value-of-cl-exe.md)。  
  
> [!NOTE]
>  不保证 1024年个字符的命令行输入的限制，以在 Windows 的未来版本中相同。  
  
## <a name="see-also"></a>请参阅  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)