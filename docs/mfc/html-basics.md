---
title: HTML 基础知识 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbe2c743f04e8fc8dc67947b9bd9d5560dd35182
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052689"
---
# <a name="html-basics"></a>HTML 基础

大多数浏览器具有查看您所浏览页面的 HTML 源的功能。 当您查看源时，将看到大量两侧是尖括号 (<>)、穿插文本的 HTML（超文本标记语言）标记。

下列步骤使用 HTML 标记生成简单网页。 在下列步骤中，您将使用“记事本”将文本键入文件中、进行一些更改、保存文件并在浏览器中重新加载页面来查看更改。

#### <a name="to-create-an-html-file"></a>若要创建某一 HTML 文件

1. 打开“记事本”或任何纯文本编辑器。

1. 从**文件**菜单中，选择**新建**。

1. 键入下列行：

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. 从**文件**菜单中，选择**保存**，并保存该文件另存为 c:\webpages\First.htm。 让文件在编辑器中处于打开状态。

1. 切换到浏览器中，并从**文件**菜单中，选择**打开**，或类型*file://C:/webpages/first.htm*浏览器的 URL 编辑框中。 你应看到一个窗口标题为“顶级 HTML 标记”的空白页。

   请注意，标记是成对的，并且包含在尖括号中。 标记不区分大小写，但通常使用大写突出标记。

   标记\<HTML > 启动文档和标记\</HTML > 结束它。 结束标记（不一定需要）与开始标记一样，但标记前具有一个正斜杠 (/)。 尖括号 (<) 与标记开头之间应没有空格。

1. 切换回记事本和之后\<头/> 行中，键入：

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. 从**文件**菜单中，选择**保存**。

1. 切换回浏览器，刷新页面。

   浏览器窗口的工作区将显示字词。 请注意，将忽略回车符。 如果要包含换行符，则必须在第一行后包括一个 `<BR>` 标记。

   有关所有步骤，请按照，插入任意位置之间的文本\<正文 > 和 \< /B o d > 若要添加到文档的正文。

9. 添加标题：

```
<H3>Here's the big picture</H3>
```

10. 使用与页面保存在同一目录中的 .gif 文件添加图像：

```
<IMG src="yourfile.gif">
```

11. 添加列表：

```
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
```

12. 若要为列表编号，请使用配对\<o L > 和\</o L > 标记来代替\<u L > 和 \< /u L > 标记。

这应当就入门了。 如果你在网页上看到一个优秀的功能，则可通过查看 HTML 源来了解如何创建该功能。 HTML 编辑器（如 Microsoft Front Page）可用于创建简单和高级页面。

这是您生成的文件的完整 HTML 源：

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

有关标记、特性和扩展的完整说明，请参阅超文本标记语言 (HTML) 规范：

[http://www.w3.org/pub/WWW/MarkUp/](http://www.w3.org/pub/www/markup/)

## <a name="see-also"></a>请参阅

[MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)

