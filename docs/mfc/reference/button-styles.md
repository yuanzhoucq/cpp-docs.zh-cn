---
title: "按钮样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BS_DEFPUSHBUTTON
- BS_NOTIFY
- BS_MULTILINE
- BS_AUTOCHECKBOX
- BS_3STATE
- BS_BITMAP
- BS_TOP
- BS_PUSHBUTTON
- BS_PUSHLIKE
- BS_AUTO3STATE
- BS_CHECKBOX
- BS_AUTORADIOBUTTON
- BS_RADIOBUTTON
- BS_OWNERDRAW
- BS_LEFT
- BS_USERBUTTON
- BS_RIGHTBUTTON
- BS_RIGHT
- BS_LEFTTEXT
- BS_TEXT
- BS_BOTTOM
- BS_GROUPBOX
- BS_FLAT
- BS_VCENTER
- BS_ICON
- BS_CENTER
dev_langs:
- C++
helpviewer_keywords:
- BS_NOTIFY constant
- BS_RIGHTBUTTON constant
- styles, button objects
- BS_USERBUTTON constant
- BS_VCENTER constant
- BS_PUSHLIKE constant
- BS_RADIOBUTTON constant
- BS_PUSHBUTTON constant
- BS_DEFPUSHBUTTON constant
- BS_LEFTTEXT constant
- button objects (CButton), button styles
- BS_AUTO3STATE constant
- BS_3STATE constant
- BS_OWNERDRAW constant
- BS_AUTORADIOBUTTON constant
- BS_GROUPBOX constant
- BS_BITMAP constant
- BS_CENTER constant
- BS_MULTILINE constant
- BS_BOTTOM constant
- BS_FLAT constant
- BS_AUTOCHECKBOX constant
- BS_RIGHT constant
- BS_CHECKBOX constant
- BS_LEFT constant
- BS_ICON constant
- BS_TOP constant
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: 20
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
ms.openlocfilehash: cdd577cd6915a1f3c1e05fae68f7fed47cc79236
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="button-styles"></a>按钮样式
本主题介绍的按钮类型和样式。  
  
## <a name="button-types"></a>按钮类型  
 下表列出的按钮类型。 （可选） 可以选择下列其中一项。 如果不指定按钮类型，默认值是`BS_PUSHBUTTON`。  
  
|类型|说明|  
|----------|-----------------|  
|`BS_3STATE`|创建具有以下三种状态的复选框按钮︰ `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 单击该按钮发送`BN_CLICKED`向所有者窗口的通知，但不更改按钮的状态。 默认情况下，关联的文本显示右侧的复选框。 若要显示的文本，左侧的复选框，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_AUTO3STATE`|创建具有以下三种状态的复选框按钮︰ `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 单击该按钮发送`BN_CLICKED`向所有者窗口的通知，并更改按钮的状态。 按钮状态的顺序的周期`BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 默认情况下，关联的文本显示右侧的复选框。 若要显示的文本，左侧的复选框，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_AUTOCHECKBOX`|创建具有两种状态的复选框按钮︰`BST_CHECKED`和`BST_UNCHECKED`。 单击该按钮发送`BN_CLICKED`向所有者窗口的通知，并更改按钮的状态。 默认情况下，关联的文本显示右侧的复选框。 若要显示的文本，左侧的复选框，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_AUTORADIOBUTTON`|创建具有两种状态的单选按钮︰`BST_CHECKED`和`BST_UNCHECKED`。 单选按钮通常用于在组与具有最多一次一个已选中的选项为每个组中。 单击该按钮发送`BN_CLICKED`向所有者窗口的通知设置已单击的单选按钮的状态`BST_CHECKED`，并将所有其他单选按钮的状态设置为按钮组中`BST_UNCHECKED`。 默认情况下，关联的文本显示右侧的单选按钮。 若要显示的文本，左侧的单选按钮，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_CHECKBOX`|创建具有两种状态的复选框按钮︰`BST_CHECKED`和`BST_UNCHECKED`。 单击该按钮发送`BN_CLICKED`向所有者窗口的通知，但不更改按钮的状态。 默认情况下，关联的文本显示右侧的复选框。 若要显示的文本，左侧的复选框，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_COMMANDLINK`|创建命令链接按钮。 命令链接按钮是特定于一个命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]主文本和便笺的主要文本之下，左侧显示一个绿色箭头。 您可以设置注释文本使用[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。|  
|`BS_DEFCOMMANDLINK`|创建命令链接按钮。 命令链接按钮是特定于一个命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]主文本和便笺的主要文本之下，左侧显示一个绿色箭头。 您可以设置注释文本使用[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。 如果按钮的对话框中，按 ENTER 键发送`BN_CLICKED`按钮不具有输入的焦点的情况下，即使对话框中的通知。|  
|`BS_DEFPUSHBUTTON`|创建具有大量的黑色边框的命令按钮。 如果按钮的对话框中，按 ENTER 键发送`BN_CLICKED`按钮不具有输入的焦点的情况下，即使对话框中的通知。|  
|`BS_DEFSPLITBUTTON`|创建拆分按钮。 拆分按钮是特定于一个命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]，其中包含靠近下拉箭头的按钮。 当单击按钮时，将执行默认命令。 当单击下拉箭头时，将显示其他命令的菜单。 如果拆分按钮在对话框中，按 ENTER 键发送`BN_CLICKED`按钮不具有输入的焦点的情况下，即使对话框中的通知|  
|`BS_GROUPBOX`|创建其他按钮可以在其中进行分组的矩形。 使用此样式关联的文本显示在该矩形的左上角。|  
|`BS_OWNERDRAW`|创建一个所有者描述的按钮。 框架将调用`DrawItem`方法时该按钮的可视方位已更改。 使用时，必须设置此样式`CBitmapButton`类。|  
|`BS_PUSHBUTTON`|创建将发送一个命令按钮`BN_CLICKED`向所有者窗口在用户单击按钮时的通知。|  
|`BS_RADIOBUTTON`|创建具有两种状态的单选按钮︰`BST_CHECKED`和`BST_UNCHECKED`。 单选按钮通常用于在组与具有最多一次一个已选中的选项为每个组中。 单击该按钮发送`BN_CLICKED`向所有者窗口的通知，但不会自动更改组中的任何按钮的状态。 默认情况下，关联的文本显示右侧的单选按钮。 若要显示的文本，左侧的单选按钮，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_SPLITBUTTON`|创建拆分按钮。 拆分按钮是特定于一个命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]，其中包含靠近下拉箭头的按钮。 当单击按钮时，将执行默认命令。 当单击下拉箭头时，将显示其他命令的菜单。|  
|`BS_USERBUTTON`|已过时，但提供与 16 位版本的 Windows 的兼容性。 基于 Win32 的应用程序应使用`BS_OWNERDRAW`相反。|  
  
## <a name="radio-button-and-check-box-styles"></a>单选按钮和复选框样式  
 下表列出了特定于单选按钮和复选框的样式。 在所有其他按钮类型，这些样式将被忽略。 （可选） 可以选择一个或多个以下。  
  
|样式|描述|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|再加上一个单选按钮或复选框样式，该文本会显示在左侧的单选按钮或复选框。|  
|`BS_RIGHTBUTTON`|再加上一个单选按钮或复选框样式，该文本会显示在左侧的单选按钮或复选框。 此样式等同于`BS_LEFTTEXT`样式。|  
|`BS_PUSHLIKE`|使复选框或单选按钮的外观和行为类似于命令按钮。 如果其状态为按钮显示为按`BST_CHECKED`、 按下和灰显其状态为时`BST_INDETERMINATE`，并释放其状态为时`BST_UNCHECKED`。|  
  
## <a name="text-alignment-styles"></a>文本对齐方式样式  
 下表列出了水平和垂直文本对齐选项。 （可选） 可以选择下列其中一项。  
  
|样式|说明|  
|-----------|-----------------|  
|`BS_LEFT`|左对齐按钮矩形中的文本。 但是，如果该按钮是一个复选框或单选按钮没有`BS_RIGHTBUTTON`样式中，文本向左单选按钮的复选框的右侧对齐。|  
|`BS_RIGHT`|右对齐按钮矩形中的文本。 但是，如果该按钮是一个复选框或单选按钮没有`BS_RIGHTBUTTON`样式，文本为右对齐单选按钮的复选框的右侧。|  
|`BS_CENTER`|居中对齐水平按钮矩形中的文本。|  
|`BS_TOP`|将文字放置在按钮矩形的顶部。|  
|`BS_BOTTOM`|将文本放在该按钮矩形的底部。|  
|`BS_VCENTER`|在按钮矩形中垂直文本居中。|  
  
## <a name="button-content-options"></a>按钮内容选项  
 下表指示在该按钮显示的内容的选项。 只能显示文本的按钮类型忽略这些样式。 （可选） 可以选择下列其中一项。  
  
|样式|说明|  
|-----------|-----------------|  
|`BS_BITMAP`|指定按钮显示位图。|  
|`BS_ICON`|指定按钮将显示一个图标。|  
|`BS_TEXT`|指定按钮显示的文本。|  
  
## <a name="other-options"></a>其他选项  
 下表列出可用于任何按钮类型的其他选项。 （可选） 可以选择一个或多个以下。  
  
|样式|描述|  
|-----------|-----------------|  
|`BS_FLAT`|指定按钮被二维和带默认阴影，以创建三维图像不会对其进行绘制。|  
|`BS_MULTILINE`|如果文本字符串太长而无法放在单独的一行按钮矩形中，包装到多个行的按钮文本。|  
|`BS_NOTIFY`|启用一个按钮将发送`BN_DBLCLK`， `BN_KILLFOCUS`，和`BN_SETFOCUS`到其父窗口的通知消息。 请注意，按钮发送`BN_CLICKED`无论是否指定此样式中的通知。|  
  
## <a name="see-also"></a>另请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create)
 [按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)   




