---
title: "编辑样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ES_READONLY
- ES_WANTRETURN
- ES_UPPERCASE
- ES_NUMBER
- ES_AUTOHSCROLL
- ES_LOWERCASE
- ES_RIGHT
- ES_MULTILINE
- ES_PASSWORD
- ES_NOHIDESEL
- ES_OEMCONVERT
- ES_LEFT
- ES_CENTER
dev_langs:
- C++
helpviewer_keywords:
- ES_WANTRETURN constant
- edit styles [MFC]
- ES_RIGHT constant
- ES_READONLY constant
- ES_PASSWORD constant
- ES_MULTILINE constant
- ES_LEFT constant
- ES_AUTOVSCROLL constant
- ES_OEMCONVERT constant
- ES_LOWERCASE constant
- ES_NUMBER constant
- ES_UPPERCASE constant
- ES_NOHIDESEL constant
- ES_AUTOHSCROLL constant
- ES_CENTER constant
ms.assetid: e6291dd6-f2cb-4ce2-ac31-32272526625c
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
ms.openlocfilehash: 275e0d2dede038bdbe9061bc8051408442aa70bf
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="edit-styles"></a>编辑样式
-   **ES_AUTOHSCROLL**自动将文本向右滚动 10 个字符时在用户键入行结尾处的字符。 当用户按 ENTER 键时，该控件将返回到位置 0 的所有文本都滚动。  
  
-   **ES_AUTOVSCROLL**自动滚动文本上移一页，当用户按 enter 键的最后一行。  
  
-   **ES_CENTER**中心中的单行或多行的文本编辑控件。  
  
-   **ES_LEFT**编辑控件的单行或多行中的左对齐文本。  
  
-   **ES_LOWERCASE**将转换为小写键入到编辑控件的所有字符。  
  
-   **ES_MULTILINE**指定多行编辑控件。 （默认值是单个行。）如果**ES_AUTOVSCROLL**指定样式、 编辑控件尽可能显示尽可能多的行和垂直滚动当用户按 ENTER 键。 如果**ES_AUTOVSCROLL**是未提供，此编辑控件将显示尽可能多的行和蜂鸣声，如果没有其他行可以显示时，按下 enter 键。 如果**ES_AUTOHSCROLL**指定样式、 多行编辑控件自动水平滚动时插入符号，超过该控件的右边缘。 若要开始新行，用户必须按 enter 键。 如果**ES_AUTOHSCROLL**是未提供，该控件自动换行到下一行的行在必要时才开始; 如果按下 enter 键，也将启动一个新行。 自动换行的位置确定的窗口大小。 如果窗口大小发生更改，换行的位置更改和文本将重新显示。 多行编辑控件可以包含滚动条。 带滚动条的编辑控件处理其自己的滚动条消息。 编辑无滚动条滚动上文所述的控件并处理由父窗口发送任何滚动信息。  
  
-   **ES_NOHIDESEL**当控件失去输入的焦点并反转所选内容，在该控件接收到输入的焦点时，一个编辑控件通常情况下，隐藏所选内容。 指定**ES_NOHIDESEL**删除此默认操作。  
  
-   **ES_NUMBER**允许仅由数字输入到编辑控件。  
  
-   **ES_OEMCONVERT**编辑控件中输入文本从 ANSI 字符集转换为的 OEM 字符集和原来的为 ANSI。 这可确保正确的字符转换，当应用程序调用`AnsiToOem`Windows 函数以将编辑控件中的 ANSI 字符串转换为 OEM 字符。 这种形式是最适用于包含文件名的编辑控件。  
  
-   **ES_PASSWORD**所有字符都显示为星号 (**\***) 键入到编辑控件。 应用程序可以使用`SetPasswordChar`成员函数来更改显示的字符。  
  
-   **ES_READONLY**可以阻止用户输入或编辑文本编辑控件中的。  
  
-   **ES_RIGHT**编辑控件中的单行或多行的右对齐文本。  
  
-   **ES_UPPERCASE**将转换为大写键入到编辑控件的所有字符。  
  
-   **ES_WANTRETURN**指定到多行编辑控件在对话框中输入文本时，在用户按 ENTER 键时插入回车符。 如果不使用此样式中，按 ENTER 键具有相同的效果与按对话框框默认按钮。 此样式不起作用的单行上编辑控件。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CEdit::Create](../../mfc/reference/cedit-class.md#create)   
 [编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)


