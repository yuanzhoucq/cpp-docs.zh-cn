---
title: LINK 命令文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8934758d8aa406ea7b7c959b1fc535cde32195b1
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894676"
---
# <a name="link-command-files"></a>LINK 命令文件

可以将命令行参数传递到命令文件的窗体中的链接。 若要指定链接器的命令文件，请使用以下语法：

> **链接\@**  <em>commandfile</em>

*Commandfile*是文本文件的名称。 无空格或制表符之间允许 at 符号 (**\@**) 和文件名。 没有默认扩展名;必须指定完整的文件名，包括任何扩展。 不能使用通配符。 使用文件名，可以指定绝对或相对路径。 链接不使用环境变量来搜索该文件。

在命令文件中，参数可以分隔空格或制表符 （在命令行中） 和由换行符。

可以在命令文件中指定的命令行全部或部分。 可以使用多个链接命令中的命令文件。 链接接受命令文件输入，如同它命令行上该位置中指定。 不能嵌套命令文件。 链接将回显命令文件的内容，除非[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)指定选项。

## <a name="example"></a>示例

以下命令以生成 DLL 在单独的命令文件中传递的对象文件和库的名称，并将第三个命令 /EXPORTS 选项的文件：

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)   
[链接器选项](../../build/reference/linker-options.md)