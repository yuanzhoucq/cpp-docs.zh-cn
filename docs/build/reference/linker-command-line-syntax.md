---
title: 链接器命令行语法
ms.date: 11/04/2016
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
ms.openlocfilehash: 55171c1f16b43e08b5c4a6b078c82f4ed08855d5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422723"
---
# <a name="linker-command-line-syntax"></a>链接器命令行语法

若要运行链接。Exe 文件，请使用以下命令语法：

```
LINK arguments
```

`arguments`包括选项和文件名，可以按任意顺序指定。 选项为已处理的第一个，则文件。 使用一个或多个空格或制表符分隔的参数。

> [!NOTE]
>  可以仅从 Visual Studio 命令提示符启动此工具。 无法从系统命令提示符或文件资源管理器中启动它。

在命令行选项选项说明符组成，短划线 （-） 或正斜杠 （/） 后, 跟的选项的名称。 不能缩写选项名称。 某些选项带自变量，在冒号 （:） 后指定。 不包含空格或选项卡允许选项规范中除 /COMMENT 选项中带引号的字符串中。 以十进制或 C 语言表示法指定数值参数。 选项名及其关键字或 filename 参数不区分大小写，但用作参数的标识符区分大小写。

要传递给链接器文件，请链接命令后在命令行上指定文件名。 可以指定绝对或相对路径与文件名，并可以在文件名中使用通配符。 如果省略句点 （.） 和文件扩展名，链接将假定.obj 用于查找文件。 链接不使用文件扩展名或缺乏进行假设内容的文件;它会通过检查，确定文件的类型并相应地对其进行处理。

link.exe 将返回零表示成功 （无错误）。  否则，链接器返回停止该链接的错误号。  例如，如果链接器生成了 LNK1104，链接器将返回 1104年。  相应地，链接器返回的错误上最小错误编号为 1000年。  返回值 128 表示操作系统或.config 文件; 的配置问题加载程序未加载 link.exe 或 c2.dll。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
