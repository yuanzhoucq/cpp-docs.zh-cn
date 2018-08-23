---
title: HTML 基础知识 |Microsoft 文档
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
ms.openlocfilehash: 9c4ebbc8e792e36461f7c52c17fa23815239e323
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929085"
---
# <a name="html-basics"></a>HTML 基础
大多数浏览器具有查看您所浏览页面的 HTML 源的功能。 当您查看源时，将看到大量两侧是尖括号 (<>)、穿插文本的 HTML（超文本标记语言）标记。  
  
 下列步骤使用 HTML 标记生成简单网页。 在下列步骤中，您将使用“记事本”将文本键入文件中、进行一些更改、保存文件并在浏览器中重新加载页面来查看更改。  
  
#### <a name="to-create-an-html-file"></a>若要创建某一 HTML 文件  
  
1.  打开“记事本”或任何纯文本编辑器。  
  
2.  从**文件**菜单上，选择**新建**。  
  
3.  键入下列行：  
  
 ```  
 <HTML>  
 <HEAD>  
 <TITLE>Top HTML Tags</TITLE>  
 </HEAD>  
 </HTML>  
 ```  
  
4.  从**文件**菜单上，选择**保存**，并将该文件保存为 c:\webpages\First.htm。 让文件在编辑器中处于打开状态。  
  
5.  浏览器中，与交换机**文件**菜单上，选择**打开**，或类型*file://C:/webpages/first.htm*浏览器的 URL 编辑框中。 你应看到一个窗口标题为“顶级 HTML 标记”的空白页。  
  
     请注意，标记是成对的，并且包含在尖括号中。 标记不区分大小写，但通常使用大写突出标记。  
  
     标记\<HTML > 文档，该标记以开始\</HTML > 结束。 结束标记（不一定需要）与开始标记一样，但标记前具有一个正斜杠 (/)。 尖括号 (<) 与标记开头之间应没有空格。  
  
6.  切换回记事本，和之后 \< /H > 行中，键入：  
  
 ```  
 <BODY>  
    HTML is swell.  
    Life is good.  
 </BODY>  
 ```  
  
7.  从**文件**菜单上，选择**保存**。  
  
8.  切换回浏览器，刷新页面。  
  
     浏览器窗口的工作区将显示字词。 请注意，将忽略回车符。 如果要包含换行符，则必须在第一行后包括一个 `<BR>` 标记。  
  
     有关所有步骤，请按照，插入任意位置之间的文本\<正文 > 和 \< /b O > 将添加到文档的正文。  
  
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
  
12. 若要为列表编号，请使用成对出现\<OL > 和\</OL > 标记代替了\<u L > 和\<u L > 标记。  
  
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

