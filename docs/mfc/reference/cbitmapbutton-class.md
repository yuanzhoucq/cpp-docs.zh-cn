---
title: "CBitmapButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBitmapButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitmaps, button controls"
  - "按钮, bitmap"
  - "CBitmapButton class"
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CBitmapButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用数字复制的图像创建按钮控件标记而不是文本。  
  
## 语法  
  
```  
class CBitmapButton : public CButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CBitmapButton::CBitmapButton](../Topic/CBitmapButton::CBitmapButton.md)|构造 `CBitmapButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CBitmapButton::AutoLoad](../Topic/CBitmapButton::AutoLoad.md)|关联在对话框中的按钮与 `CBitmapButton` 选件类的对象，按名称加载位图，并调整按钮以位图。|  
|[CBitmapButton::LoadBitmaps](../Topic/CBitmapButton::LoadBitmaps.md)|通过填写一个或多个名为位图资源从应用程序的资源文件和附加位图初始化对象到对象。|  
|[CBitmapButton::SizeToContent](../Topic/CBitmapButton::SizeToContent.md)|调整按钮的大小以容纳位图。|  
  
## 备注  
 `CBitmapButton` 对象包含四个位图，包含不同状态的图像按钮可以假定:\(普通\)，拉\(或选择\)，居中并禁用。  只需要第一个位图;其他是可选的。  
  
 位图按钮图像位于图像以及图像周围包括边框。  该边框通常作为在显示按钮的状态的效果。  例如，该焦点状态的位图通常是与个状态的，但与边框的虚线矩形嵌入或一个重新实线在边框。  该禁用状态的位图通常类似于个状态的，但具有较低的对比度\(如一个灰显的或的灰色菜单中选择）。  
  
 这些位图可以为任意大小，但是，任何处理，则相同大小与该状态的位图。  
  
 多个应用程序要求位图图像的不同组合:  
  
|向上键|向下|Focused|禁用|Application|  
|---------|--------|-------------|--------|-----------------|  
|×||||位图|  
|×|×|||不 **WS\_TABSTOP** 样式的按钮|  
|×|×|×|×|对话框按钮是任何状态|  
|×|×|×||具有 **WS\_TABSTOP** 样式的对话框按钮|  
  
 在创建位图按钮控件，请将 **BS\_OWNERDRAW** 样式指定所有者绘制按钮。  这会使Windows发送按钮的 `WM_MEASUREITEM` 和 `WM_DRAWITEM` 信息;结构处理这些消息和管理按钮的外观您的。  
  
### 创建位图按钮控件在窗口的工作区  
  
1.  启动按钮的一到四个位图图像。  
  
2.  构造 [CBitmapButton](../Topic/CBitmapButton::CBitmapButton.md) 对象。  
  
3.  调用 [创建](../Topic/CButton::Create.md) 函数创建Windows按钮控件并将其附加到 `CBitmapButton` 对象。  
  
4.  在位图按钮构造后，调用 [LoadBitmaps](../Topic/CBitmapButton::LoadBitmaps.md) 成员函数加载位图资源。  
  
### 包括位图按钮控件在对话框  
  
1.  启动按钮的一到四个位图图像。  
  
2.  在确定的所有者描述按钮创建一个对话框模板所需位图按钮的位置。  按钮的大小在模板的无关紧要。  
  
3.  将按钮的阐释一个值\(如“**MYIMAGE**”并定义按钮的一个符号\(如\) **IDC\_MYIMAGE**。  
  
4.  在应用程序的资源脚本，请为可为生成的每个图像追加构造的ID之一个字母“U”，“，" D” F “，”或“X” \(对于，滚动，居中并禁用\)用于按钮标题的字符串在第3.步。  对于按钮标题“**MYIMAGE**，”例如，ID为“**MYIMAGEU**，”**MYIMAGED**，”**MYIMAGEF**，”和“**MYIMAGEX**”。您 **must** 指定您在双引号中的位图ID。  否则资源编辑器将整数到资源，而MFC将失败，当加载图像时。  
  
5.  在应用程序的对话框选件类\(从派生 `CDialog`\)中，添加一 `CBitmapButton` 成员对象。  
  
6.  在 `CDialog` 对象的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 实例，请调用 `CBitmapButton` 对象的 [自动上载](../Topic/CBitmapButton::AutoLoad.md) 功能，使用参数，按钮的控件ID和 `CDialog` 对象的 **this** 指针。  
  
 如果希望处理Windows通知消息，例如 **BN\_CLICKED**，发送由位图按钮控件绑定到其父\(通常从 **CDialog\)**派生的选件类，请添加到 `CDialog`派生的对象每个消息的消息映射项和消息处理程序成员函数。  `CBitmapButton` 对象发送的通知是一样的。[CButton](../../mfc/reference/cbutton-class.md) 对象发送的小。  
  
 选件类 [CToolBar](../../mfc/reference/ctoolbar-class.md) 接受其他方法向位图按钮。  
  
 有关 `CBitmapButton`的更多信息，请参见[控件](../../mfc/controls-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例CTRLTEST](../../top/visual-cpp-samples.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)