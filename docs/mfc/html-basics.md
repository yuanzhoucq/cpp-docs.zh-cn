---
title: HTML 基础
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 6d3a692eab47a1309ee0248b51ab8563fb077d5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377250"
---
# <a name="html-basics"></a>HTML 基础

大多数浏览器具有查看您所浏览页面的 HTML 源的功能。 当您查看源时，您将看到许多 HTML（超文本标记语言）标记，这些标记由角括号（<>）包围，并穿插在文本中。

下列步骤使用 HTML 标记生成简单网页。 在下列步骤中，您将使用“记事本”将文本键入文件中、进行一些更改、保存文件并在浏览器中重新加载页面来查看更改。

#### <a name="to-create-an-html-file"></a>创建 HTML 文件

1. 打开“记事本”或任何纯文本编辑器。

1. 在 **"文件"** 菜单中，选择 **"新建**"。

1. 键入下列行：

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. 在 **"文件"** 菜单中，选择 **"保存**"并将文件另存为 c：_@网页\First.htm。 让文件在编辑器中处于打开状态。

1. 切换到浏览器，并从 **"文件**"菜单中选择 **"打开**"，或在浏览器的 URL 编辑框中键入*file://C:/webpages/first.htm。* 你应看到一个窗口标题为“顶级 HTML 标记”的空白页。

   请注意，标记是成对的，并且包含在尖括号中。 标记不区分大小写，但通常使用大写突出标记。

   标记\<HTML>启动文档，标记\</HTML>结束它。 结束标记（不一定需要）与开始标记一样，但标记前具有一个正斜杠 (/)。 角度支架 （<） 和标记的开头之间不应有空格。

1. 切换回记事本，在\</HEAD> 行后，键入：

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. 在 **"文件"** 菜单中，选择 **"保存**"。

1. 切换回浏览器，刷新页面。

   浏览器窗口的工作区将显示字词。 请注意，将忽略回车符。 如果要包含换行符，则必须在第一行后包括一个 `<BR>` 标记。

   对于以下所有步骤，请在 BODY> 和\<\</BODY>之间任意位置插入文本以添加到文档正文中。

1. 添加标题：

    ```html
    <H3>Here's the big picture</H3>
    ```

1. 使用与页面保存在同一目录中的 .gif 文件添加图像：

    ```html
    <IMG src="yourfile.gif">
    ```

1. 添加列表：

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. 要对列表进行编号，请使用配对\<的 OL \<>和 /OL>\<标记来代替\<UL>和 /UL>标记。

这应当就入门了。 如果你在网页上看到一个优秀的功能，则可通过查看 HTML 源来了解如何创建该功能。 HTML 编辑器（如 Microsoft Front Page）可用于创建简单和高级页面。

这是您生成的文件的完整 HTML 源：

```html
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

[最新版本的 HTML](https://www.w3.org/TR/html/)在 W3C.org。

## <a name="see-also"></a>另请参阅

[MFC 互联网编程基础知识](../mfc/mfc-internet-programming-basics.md)
