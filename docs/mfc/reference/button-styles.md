---
title: "按钮样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- BS_NOTIFY constant [MFC]
- BS_RIGHTBUTTON constant [MFC]
- styles [MFC], button objects
- BS_USERBUTTON constant [MFC]
- BS_VCENTER constant [MFC]
- BS_PUSHLIKE constant [MFC]
- BS_RADIOBUTTON constant [MFC]
- BS_PUSHBUTTON constant [MFC]
- BS_DEFPUSHBUTTON constant [MFC]
- BS_LEFTTEXT constant [MFC]
- button objects (CButton), button styles
- BS_AUTO3STATE constant [MFC]
- BS_3STATE constant [MFC]
- BS_OWNERDRAW constant [MFC]
- BS_AUTORADIOBUTTON constant [MFC]
- BS_GROUPBOX constant [MFC]
- BS_BITMAP constant [MFC]
- BS_CENTER constant [MFC]
- BS_MULTILINE constant [MFC]
- BS_BOTTOM constant [MFC]
- BS_FLAT constant [MFC]
- BS_AUTOCHECKBOX constant [MFC]
- BS_RIGHT constant [MFC]
- BS_CHECKBOX constant [MFC]
- BS_LEFT constant [MFC]
- BS_ICON constant [MFC]
- BS_TOP constant [MFC]
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9ed2dcffbcd45215008b3d0caa802a5384367b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="button-styles"></a>按钮样式
本主题介绍按钮类型和样式。  
  
## <a name="button-types"></a>按钮类型  
 下表列出按钮类型。 根据需要，你可以选择下列其中一项。 如果未指定按钮类型，默认值是`BS_PUSHBUTTON`。  
  
|类型|描述|  
|----------|-----------------|  
|`BS_3STATE`|创建具有三种状态的复选框按钮： `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 单击该按钮将发送`BN_CLICKED`向所有者窗口的通知，但不更改按钮的状态。 默认情况下，关联的文本将显示右侧的复选框。 若要显示到左侧的复选框的文本，请使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_AUTO3STATE`|创建具有三种状态的复选框按钮： `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 单击该按钮将发送`BN_CLICKED`向所有者窗口的通知，并更改按钮的状态。 按钮状态顺序排列的周期`BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 默认情况下，关联的文本将显示右侧的复选框。 若要显示到左侧的复选框的文本，请使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_AUTOCHECKBOX`|创建具有两个状态的复选框按钮：`BST_CHECKED`和`BST_UNCHECKED`。 单击该按钮将发送`BN_CLICKED`向所有者窗口的通知，并更改按钮的状态。 默认情况下，关联的文本将显示右侧的复选框。 若要显示到左侧的复选框的文本，请使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_AUTORADIOBUTTON`|创建具有两个状态的单选按钮：`BST_CHECKED`和`BST_UNCHECKED`。 单选按钮通常用在组中，且具有一个已选中的选项，一次最多每个组。 单击该按钮将发送`BN_CLICKED`向所有者窗口的通知设置被单击的单选按钮的状态`BST_CHECKED`，设置按钮组的所有其他单选按钮的状态和`BST_UNCHECKED`。 默认情况下，关联的文本将显示右侧的单选按钮。 若要显示到左侧的单选按钮的文本，请使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_CHECKBOX`|创建具有两个状态的复选框按钮：`BST_CHECKED`和`BST_UNCHECKED`。 单击该按钮将发送`BN_CLICKED`向所有者窗口的通知，但不更改按钮的状态。 默认情况下，关联的文本将显示右侧的复选框。 若要显示到左侧的复选框的文本，请使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_COMMANDLINK`|创建命令链接按钮。 命令链接按钮是特定于的命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]的主要文本和注释的主文本的下方左侧显示一个绿色箭头。 你可以注意文本使用设置[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。|  
|`BS_DEFCOMMANDLINK`|创建命令链接按钮。 命令链接按钮是特定于的命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]的主要文本和注释的主文本的下方左侧显示一个绿色箭头。 你可以注意文本使用设置[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。 如果按钮是在对话框中，并按 enter 键密钥发送`BN_CLICKED`到按钮不具有输入的焦点的情况下，即使对话框中的通知。|  
|`BS_DEFPUSHBUTTON`|创建一个具有大量的黑色边框的命令按钮。 如果按钮是在对话框中，并按 enter 键密钥发送`BN_CLICKED`到按钮不具有输入的焦点的情况下，即使对话框中的通知。|  
|`BS_DEFSPLITBUTTON`|创建一个拆分按钮。 拆分按钮是特定于的命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]包含靠近下拉箭头的按钮。 当单击按钮时，将执行的默认命令。 当您单击下拉箭头时，显示的其他命令菜单。 如果拆分按钮在对话框中，并按 enter 键密钥发送`BN_CLICKED`到按钮不具有输入的焦点的情况下，即使对话框中的通知|  
|`BS_GROUPBOX`|创建一个矩形其他按钮可以在其中进行分组。 使用此样式关联的文本显示在矩形的左上角。|  
|`BS_OWNERDRAW`|创建一个所有者绘制的按钮。 框架调用`DrawItem`方法时的按钮的可视方位已更改。 使用时，必须设置此样式`CBitmapButton`类。|  
|`BS_PUSHBUTTON`|创建命令按钮发送`BN_CLICKED`向所有者窗口用户单击按钮时的通知。|  
|`BS_RADIOBUTTON`|创建具有两个状态的单选按钮：`BST_CHECKED`和`BST_UNCHECKED`。 单选按钮通常用在组中，且具有一个已选中的选项，一次最多每个组。 单击该按钮将发送`BN_CLICKED`向所有者窗口的通知，但不会自动更改组中任何按钮的状态。 默认情况下，关联的文本将显示右侧的单选按钮。 若要显示到左侧的单选按钮的文本，请使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`样式。|  
|`BS_SPLITBUTTON`|创建一个拆分按钮。 拆分按钮是特定于的命令按钮[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]包含靠近下拉箭头的按钮。 当单击按钮时，将执行的默认命令。 当您单击下拉箭头时，显示的其他命令菜单。|  
|`BS_USERBUTTON`|过时，但提供的 16 位版本的 Windows 兼容性。 基于 Win32 的应用程序应使用`BS_OWNERDRAW`相反。|  
  
## <a name="radio-button-and-check-box-styles"></a>单选按钮和复选框样式  
 下表列出了特定于单选按钮和复选框的样式。 在所有其他按钮类型情况下，这些样式将被忽略。 你可以根据需要选择一个或多个以下。  
  
|样式|描述|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|与单选按钮或复选框样式结合使用，文本会显示在左侧的单选按钮或复选框。|  
|`BS_RIGHTBUTTON`|与单选按钮或复选框样式结合使用，文本会显示在左侧的单选按钮或复选框。 此样式等同于`BS_LEFTTEXT`样式。|  
|`BS_PUSHLIKE`|使复选框或单选按钮的外观和行为类似于命令按钮。 其状态为时，该按钮显示按下`BST_CHECKED`、 按下和灰显其状态为时`BST_INDETERMINATE`，并释放其状态为时`BST_UNCHECKED`。|  
  
## <a name="text-alignment-styles"></a>文本对齐方式样式  
 下表列出了水平和垂直文本对齐方式选项。 根据需要，你可以选择下列其中一项。  
  
|样式|描述|  
|-----------|-----------------|  
|`BS_LEFT`|左对齐按钮矩形中的文本。 但是，如果按钮是一个复选框或单选按钮，则不具有`BS_RIGHTBUTTON`样式，文本向左对齐的复选框或单选按钮的右侧。|  
|`BS_RIGHT`|右对齐按钮矩形中的文本。 但是，如果按钮是一个复选框或单选按钮，则不具有`BS_RIGHTBUTTON`样式，文本为右对齐的复选框或单选按钮的右侧。|  
|`BS_CENTER`|中心水平按钮矩形中的文本。|  
|`BS_TOP`|放置的按钮矩形的顶部的文本。|  
|`BS_BOTTOM`|将文本放在底部的按钮矩形。|  
|`BS_VCENTER`|中心垂直按钮矩形中的文本。|  
  
## <a name="button-content-options"></a>按钮内容选项  
 下表列出指示按钮中显示的内容的选项。 仅显示文本的按钮类型忽略这些样式。 根据需要，你可以选择下列其中一项。  
  
|样式|描述|  
|-----------|-----------------|  
|`BS_BITMAP`|指定按钮显示位图。|  
|`BS_ICON`|指定按钮显示一个图标。|  
|`BS_TEXT`|指定按钮显示文本。|  
  
## <a name="other-options"></a>其他选项  
 下表列出可用于任何按钮类型的其他选项。 你可以根据需要选择一个或多个以下。  
  
|样式|描述|  
|-----------|-----------------|  
|`BS_FLAT`|指定按钮被二维和带默认阴影，以创建三维映像不会对其进行绘制。|  
|`BS_MULTILINE`|如果文本字符串太长，无法放在单个行中的按钮矩形，包装到多个行的按钮文本。|  
|`BS_NOTIFY`|启用一个按钮将发送`BN_DBLCLK`， `BN_KILLFOCUS`，和`BN_SETFOCUS`到其父窗口的通知消息。 请注意，按钮发送`BN_CLICKED`无论是否指定此样式的通知。|  
  
## <a name="see-also"></a>请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create) [按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)   



