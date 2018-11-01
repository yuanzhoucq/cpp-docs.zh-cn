---
title: 点指令
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 18688afedfe076ea2e4485471ffbe92dc2e09a2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542865"
---
# <a name="dot-directives"></a>点指令

指定块外的说明，在行的开始点指令。 点指令以句点开头 (。 ) 后, 跟一个冒号 （:）。 允许空格和制表符。 点指令名称区分大小写，大写字母。

|指令|目标|
|---------------|-------------|
|**.忽略：**|忽略非零退出代码返回的命令，从指定到生成文件的末尾的位置。 默认情况下，如果命令返回非零退出代码，NMAKE 暂停。 若要还原错误检查，请使用 **！CMDSWITCHES**。 若要忽略的单个命令的退出代码，请使用短划线 （-） 修饰符。 若要忽略整个文件的退出代码，请使用 / 我。|
|**.贵重：** *目标*|将保留*目标*磁盘上的命令将其更新都将暂停; 如果不起如果命令通过删除该文件来处理中断。 使用一个或多个空格或制表符分隔的目标名称。 默认情况下，NMAKE 删除目标，如果按 CTRL + C 或 CTRL + BREAK 中断生成。 每次使用都 **。宝贵**适用于整个生成文件; 多个规范是累积性。|
|**.无提示：**|取消显示执行的命令，从指定到生成文件的末尾的位置。 默认情况下，NMAKE 显示它调用的命令。 若要还原回显，请使用 **！CMDSWITCHES**。 若要禁止显示单个命令的回显，请使用**@** 修饰符。 若要取消整个文件的回显，请使用/秒。|
|**.后缀：** `list`|列出用于推断规则匹配; 扩展预定义包含以下扩展：.exe.obj.asm.c.cpp.cxx.bas.cbl。 有关.pas.res.rc.f.f90|

若要更改 **。后缀**列表顺序，或若要指定新列表，请清除该列表并指定一个新的设置。 若要清除列表，指定在冒号后没有扩展：

```
.SUFFIXES :
```

若要将其他后缀添加到列表的末尾，指定

```
.SUFFIXES : suffixlist
```

其中*suffixlist*是其他后缀，由一个或多个空格或制表符分隔的列表。 若要查看的当前设置 **。后缀**，使用 /P.运行 NMAKE

## <a name="see-also"></a>请参阅

[NMAKE 参考](../build/nmake-reference.md)