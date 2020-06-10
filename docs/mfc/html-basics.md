---
title: HTML 基础
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 29ca2e3df4981db22a10281ba2a2938fc91d5b46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620004"
---
# <a name="html-basics"></a>HTML 基础

大多数浏览器具有查看您所浏览页面的 HTML 源的功能。 查看源时，将看到多个 HTML （超文本标记语言）标记，这些标记由尖括号（<>）括起来，并与文本交错。

下列步骤使用 HTML 标记生成简单网页。 在下列步骤中，您将使用“记事本”将文本键入文件中、进行一些更改、保存文件并在浏览器中重新加载页面来查看更改。

#### <a name="to-create-an-html-file"></a>创建 HTML 文件

1. 打开“记事本”或任何纯文本编辑器。

1. 从 "**文件**" 菜单中选择 "**新建**"。

1. 键入下列行：

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. 从 "**文件**" 菜单中选择 "**保存**"，并将文件另存为 c:\webpages\First.htm。 让文件在编辑器中处于打开状态。

1. 切换到浏览器，然后从 "**文件**" 菜单中选择 "**打开**"，或在浏览器的 URL 编辑框中键入*file://C:/webpages/first.htm* 。 你应看到一个窗口标题为“顶级 HTML 标记”的空白页。

   请注意，标记是成对的，并且包含在尖括号中。 标记不区分大小写，但通常使用大写突出标记。

   标记将 \<HTML> 启动文档，标记将 \</HTML> 结束。 结束标记（不一定需要）与开始标记一样，但标记前具有一个正斜杠 (/)。 尖括号（<）和标记开头之间不应有空格。

1. 切换回记事本，然后在行后面 \</HEAD> 键入：

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. 从 "**文件**" 菜单中选择 "**保存**"。

1. 切换回浏览器，刷新页面。

   浏览器窗口的工作区将显示字词。 请注意，将忽略回车符。 如果要包含换行符，则必须在第一行后包括一个 `<BR>` 标记。

   对于下面的所有步骤，请在和之间插入文本， \<BODY> 并 \</BODY> 将其添加到文档正文。

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

1. 若要改为对列表进行编号，请使用成对的 \<OL> 和 \</OL> 标记代替 \<UL> 和 \</UL> 标记。

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

W3C.org 上[的最新发布的 HTML 版本](https://www.w3.org/TR/html/)。

## <a name="see-also"></a>另请参阅

[MFC Internet 编程基础知识](mfc-internet-programming-basics.md)
