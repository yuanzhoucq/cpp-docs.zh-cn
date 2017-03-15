---
title: "HTML 基础 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HTML, 关于 HTML"
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HTML 基础
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数浏览器需要检查您浏览页面的 HTML 源的功能。  当您查看将显示大量的 HTML 源 \(HyperText Markup Language\)，标记是由尖括号 \(\<\>\)，与使用文本。  
  
 在使用生成简单网页的 HTML 标记下的步骤。  在以下步骤，您将键入纯文本到记事本的文件，使某种更改，保存文件，并在浏览器中重新加载该页才能看到更改。  
  
#### 创建 HTML 文件  
  
1.  打开记事本或所有纯文本编辑器使用。  
  
2.  从**“文件”**菜单中选择“保存”`New`。  
  
3.  键入以下行：  
  
    ```  
    <HTML>  
    <HEAD>  
    <TITLE>Top HTML Tags</TITLE>  
    </HEAD>  
    </HTML>  
    ```  
  
4.  从 **文件** 菜单中，选择 **保存**，将该文件保存为 c:\\webpages\\First.htm.  在“代码编辑器”中打开文件。  
  
5.  切换到浏览器并从 **文件** 菜单中，选择 **打开**或键入在浏览器的 URL 编辑框的 `file://C:/webpages/first.htm`。  您应看到的窗口标题“Top\-level HTML 标记的一个空白页”。  
  
     请注意名为尖括号中成对的和中。  标记不区分大小写，但通常大小写进行标记引人注意。  
  
     HTML\> 文档中，开始标记 \<，并且标记 \<\/HTML\> 关闭它。  结束标记 \(\) 不需要始终与的开始标记，但在某些情况下，一个正斜杠 \(\/\/\) 将标记前面。  不应具有在尖括号 \(\<\) 和标记的开头之间的空间。  
  
6.  回记事本的开关，并且，在 \<\/HEAD\> 行类型后：  
  
    ```  
    <BODY>  
    HTML is swell.  
    Life is good.  
    </BODY>  
    ```  
  
7.  从**“文件”**菜单中选择**“保存”**。  
  
8.  回浏览器切换和刷新页面。  
  
     Word 将显示在浏览器窗口的工作区。  请注意、回车符被忽略。  如果要包含换行符，必须包括 `<BR>` 标记，在第一行后面。  
  
     对于下面的所有步骤，在 \<BODY\> 和 \<\/BODY\> 之间的任何位置插入文本以添加文档主体。  
  
9. 添加标题：  
  
    ```  
    <H3>Here's the big picture</H3>  
    ```  
  
10. 添加图像，使用位于目录保存的 .gif 文件和页相同：  
  
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
  
12. 若要计算列表，请在 \<UL\> 和 \<\/UL\> 标记位置使用匹配的 \<OL\> \/OL\> 和 \<标记。  
  
 这应您入门。  如果看到在网页上的功能，则可以查看它如何通过检查 HTML 源创建。  HTML 编辑器 \(Front Page Microsoft 可用于创建简单页面和高级。  
  
 这是在生成的文件的完整 HTML 源：  
  
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
  
 对于标记的完整说明，属性和扩展，请参见 HyperText Markup Language \(HTML\) 规范：  
  
 [http:\/\/www.w3.org\/pub\/WWW\/MarkUp\/](http://www.w3.org/pub/WWW/MarkUp/)  
  
## 请参阅  
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)