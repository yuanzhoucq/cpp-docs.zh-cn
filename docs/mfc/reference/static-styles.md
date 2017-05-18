---
title: "静态样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SS_SUNKEN
- SS_CENTER
- SS_ENHMETAFILE
- SS_RIGHT
- SS_BLACKRECT
- SS_LEFTNOWORDWRAP
- SS_GRAYFRAME
- SS_USERITEM
- SS_GRAYRECT
- SS_WHITEFRAME
- SS_ETCHEDFRAME
- SS_ETCHEDVERT
- SS_WHITERECT
- SS_PATHELLIPSIS
- SS_WORDELLIPSIS
- SS_NOPREFIX
- SS_BITMAP
- SS_SIMPLE
- SS_CENTERIMAGE
- SS_BLACKFRAME
- SS_OWNERDRAW
- SS_REALSIZEIMAGE
- SS_RIGHTJUST
- SS_ICON
- SS_NOTIFY
- SS_ETCHEDHORZ
- SS_LEFT
- SS_ENDELLIPSIS
dev_langs:
- C++
helpviewer_keywords:
- SS_ICON constant
- SS_WHITEFRAME constant
- SS_BLACKFRAME constant
- SS_ETCHEDHORZ constant
- SS_OWNERDRAW constant
- SS_BITMAP constant
- SS_NOPREFIX constant
- SS_NOTIFY constant
- SS_CENTER constant
- SS_REALSIZEIMAGE constant
- SS_ETCHEDFRAME constant
- SS_CENTERIMAGE constant
- SS_SUNKEN constant
- SS_ENDELLIPSIS constant
- SS_WORDELLIPSIS constant
- SS_WHITERECT constant
- SS_ETCHEDVERT constant
- SS_GRAYFRAME constant
- SS_LEFTNOWORDWRAP constant
- SS_LEFT constant
- SS_SIMPLE constant
- static styles
- SS_ENHMETAFILE constant
- SS_GRAYRECT constant
- SS_USERITEM constant
- SS_PATHELLIPSIS constant
- SS_BLACKRECT constant
- SS_RIGHT constant
- SS_RIGHTJUST constant
ms.assetid: a1114548-fc6d-491d-8c46-21d11b8574f5
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ad34c688fdfd3c2b4c81a0a03fbce53a905162ad
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="static-styles"></a>静态样式
-   **SS_BITMAP**指定位图是在静态控件中显示。 给定的文本是位图 （而不是文件名） 的资源文件中的其他位置定义的名称。 该样式将忽略 nWidth 参数和 nHeight 参数;控件自动调整自身大小以容纳该位图。  
  
-   **SS_BLACKFRAME**与框架窗口框架一样的颜色绘制指定的框。 默认为黑色。  
  
-   **SS_BLACKRECT**指定用来绘制窗口框架的颜色填充矩形。 默认为黑色。  
  
-   **SS_CENTER**指定一个简单的矩形，并显示给定的矩形中居中的文本。 文本显示之前设置。 将会超过行末尾的单词自动换到下一步居中行的开头。  
  
-   **SS_CENTERIMAGE**指定，是否位图或图标小于静态控件的客户端区域，则客户端区域的其余部分用位图或图标的左上角的像素的颜色填充。 如果静态控件中包含单个文本行，则该控件的工作区中垂直居中文本。  
  
-   **SS_ENDELLIPSIS**或**SS_PATHELLIPSIS**替换给定字符串的一部分使用省略号，如有必要，以使其适合指定的矩形的结果。  
  
     您可以指定**SS_END_ELLIPSIS**来替换该字符串末尾的字符或**SS_PATHELLIPSIS**来替换该字符串中间的字符。 如果该字符串包含反斜杠 (\\) 个字符， **SS_PATHELLIPSIS**保留尽可能多的文本在最后一个反斜杠后尽可能。  
  
-   **SS_ENHMETAFILE**指定静态控件中显示增强的图元文件。 给定的文本是图元文件的名称。 增强型图元文件静态控件具有固定的大小，则图元文件进行缩放以适合静态控件工作区。  
  
-   **SS_ETCHEDFRAME**绘制静态控件使用的框架**EDGE_ETCHED**边缘样式。  
  
-   **SS_ETCHEDHORZ**绘制静态控件使用的上边缘和下边缘**EDGE_ETCHED**边缘样式。  
  
-   **SS_ETCHEDVERT**绘制使用 EDGE_ETCHED 边缘样式的静态控件左、 右边缘。  
  
-   **SS_GRAYFRAME**带有框架使用相同的颜色为屏幕背景 （桌面） 绘制指定的框。 默认为灰色。  
  
-   **SS_GRAYRECT**指定用来填充屏幕背景的颜色填充矩形。 默认为灰色。  
  
-   **SS_ICON**指定显示在对话框中的图标。 给定的文本是一个图标 （而不是文件名） 的资源文件中的其他位置定义的名称。 `nWidth`和`nHeight`参数将被忽略; 图标自动调整自身大小。  
  
-   **SS_LEFT**指定一个简单的矩形，并显示给定的文本的矩形中刷新从右向左。 文本显示之前设置。 将会超过行末尾的单词自动换到下一步刷新左行的开头。  
  
-   **SS_LEFTNOWORDWRAP**指定一个简单的矩形，并显示给定的文本的矩形中刷新从右向左。 选项卡都展开之后，但不是包装的单词。 超出行末尾的文本被截断。  
  
-   **SS_NOPREFIX**除非指定此样式，则 Windows 会将解释要加速器前缀字符的控件的文本中的任何 and 符 （&） 字符。 在这种情况下，删除与符号，并在字符串中的下一个字符加下划线。 如果静态控件将包含文本，不需要此功能， **SS_NOPREFIX**可能添加。 此静态控件样式可能与任何定义的静态控件包括在内。 您可以组合使用**SS_NOPREFIX**具有其他样式通过使用按位 OR 运算符。 这是最常使用的当需要在对话框中的静态控件中显示文件名或其他可能包含 and 符的字符串时。  
  
-   **SS_NOTIFY**向父窗口发送**STN_CLICKED**， **STN_DBLCLK**， **STN_DISABLE**，和**STN_ENABLE**通知邮件时在用户单击或双击该控件。  
  
-   **SS_OWNERDRAW**指定静态控件的所有者负责绘制控件。 所有者窗口中接收`WM_DRAWITEM`消息时该控件需要绘制。  
  
-   **SS_REALSIZEIMAGE**禁止静态图标或位图控件 (即，具有的静态控件**SS_ICON**或**SS_BITMAP**样式) 从在加载或绘制时在正调整大小。 如果图标或位图大于目标区域，裁剪图像。  
  
-   **SS_RIGHT**指定一个简单的矩形，并显示给定的文本的矩形中刷新右。 文本显示之前设置。 将会超过行末尾的单词自动换到下一步刷新右行的开头。  
  
-   **SS_RIGHTJUST**指定具有静态控件的右下角**SS_BITMAP**或**SS_ICON**样式是保持固定调整控件的大小。 仅的顶部和左侧边调整以适应新位图或图标。  
  
-   **SS_SIMPLE**指定一个简单的矩形，并显示单行文本的矩形中刷新从右向左。 文本行不能缩短或以任何方式发生改变。 (不处理控件的父窗口或对话框中，必须`WM_CTLCOLOR`消息。)  
  
-   **SS_SUNKEN**半凹陷周围绘制边框静态控件。  
  
-   **SS_USERITEM**指定用户定义的项。  
  
-   **SS_WHITEFRAME**带有框架以与窗口背景颜色相同绘制指定的框。 默认值为白色。  
  
-   **SS_WHITERECT**指定用来填充窗口背景的颜色填充矩形。 默认值为白色。  
  
-   **SS_WORDELLIPSIS**截断文本的不符合并将省略号。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CStatic::Create](../../mfc/reference/cstatic-class.md#create)   
 [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)   
 [静态控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760773)


