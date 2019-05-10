---
title: 定义宏的位置
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: dc03644adea4619b3eabe33c481d71f704a9f410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316361"
---
# <a name="where-to-define-macros"></a>定义宏的位置

在命令行、 命令文件，生成文件或 Tools.ini 文件中定义的宏。

在生成文件或 Tools.ini 文件中，每个宏的定义必须出现在单独的行，并且不能以空格或制表符开头。忽略空格或等号两侧的选项卡。 所有[字符的字符串](defining-an-nmake-macro.md)都是文本，包括引号和嵌入的空格。

在命令行或命令文件中，空格和制表符分隔自变量并不能出现在等号。 如果`string`有嵌入空格或制表符，将该字符串本身或整个宏括在双引号 ("")。

## <a name="see-also"></a>请参阅

[定义 NMAKE 宏](defining-an-nmake-macro.md)
