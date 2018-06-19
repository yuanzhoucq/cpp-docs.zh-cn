---
title: TN031： 控件条 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.bars
dev_langs:
- C++
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1d5cc113177a9653e709c14f66682959276e7ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385321"
---
# <a name="tn031-control-bars"></a>TN031：控件条
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释描述 MFC 中的控件条类：常规 [CControlBar](#_mfcnotes_ccontrolbar)、 [CStatusBar](#_mfcnotes_cstatusbar)、 [CToolBar](#_mfcnotes_ctoolbar)、 [CDialogBar](#_mfcnotes_cdialogbar)和 **CDockBar**。  
  
## <a name="_mfcnotes_ccontrolbar"></a> CControlBar 
  
 **ControlBar** 是 `CWnd`派生类，其：  
  
-   与框架窗口的顶端或底端对齐。  
  
-   可能包含为基于 HWND 的控件（例如， `CDialogBar`）或基于非`HWND` （例如， `CToolBar`、 `CStatusBar`）的项的子项。  
  
 控件条支持附加样式：  
  
- `CBRS_TOP` （默认值）将控件条固定到顶端。  
  
- `CBRS_BOTTOM` 将控件条固定到底端。  
  
- `CBRS_NOALIGN` 当父级重设大小时，将不会重新定位控件条。  
  
 从 `CControlBar` 派生的类提供更有趣的实现：  
  
- `CStatusBar` 一个状态栏，项是包含文本的状态栏窗格。  
  
- `CToolBar` 一个工具栏，项是行内对齐的位图按钮。  
  
- `CDialogBar` 一个像工具栏一样的框架，其中包含标准窗口控件（通过对话框模板资源创建）。  
  
- **CDockBar** 其他 `CControlBar` 派生对象的通用停靠区域。 此类中可用的特定成员函数和变量可能在将来的版本中发生更改。  
  
 所有控件条对象/窗口都将是某个父框架窗口的子窗口。 它们通常将作为同级添加到框架的工作区（例如，MDI 客户端或视图）。 控件条的子窗口 ID 很重要。 控件条的默认布局仅对 ID 位于 **AFX_IDW_CONTROLBAR_FIRST** 到 **AFX_IDW_CONTROLBAR_LAST**范围的控件条起作用。 请注意，即使具有 256 个控件条 ID，其中前 32 个控件条 ID 也是特定的，因为它们由打印预览体系结构直接支持。  
  
 `CControlBar` 类将提供具有下列作用的标准实现：  
  
-   将控件条对齐到框架的顶端、底端或任一端。  
  
-   分配控件项数组。  
  
-   支持派生类的实现。  
  
 C++ 控件条对象一般将作为 `CFrameWnd` 派生类的成员嵌入，并且将在销毁父 `HWND` 和对象时得到清理。 如果需要在堆上分配控件条对象，则可以将 **m_bAutoDestruct** 成员设置为 **TRUE** ，以便在销毁**时使控件条“删除此项”**`HWND` 。  
  
> [!NOTE]
>  如果创建自己的 `CControlBar`派生类，而不使用 MFC 的派生类之一（如 `CStatusBar`、 `CToolBar`或 `CDialogBar`），则您需要设置 `m_dwStyle` 数据成员。 这可通过重写 **Create**来完成：  
  
```  
// CMyControlBar is derived from CControlBar  
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)  
{  
    m_dwStyle = dwStyle;  
 
 .  
 .  
 .  
}  
```  
  
 **控件条布局算法**  
  
 控件条的布局算法非常简单。 框架窗口将一条 **WM_SIZEPARENT** 消息发送给控件条范围内的所有子级。 除此消息之外，还将传递指向父级矩形工作区的指针。 此信息发送给处于 Z 顺序的子级。 控件条子级使用此信息来确定自己的位置并缩减父级工作区的范围。 常规工作区剩下的最后一个矩形（小于控件条）将用于确定主要工作区窗口的位置（通常是 MDI 客户端、视图或拆分窗口）。  
  
 有关更多详细信息，请参阅 `CWnd::RepositionBars` 和 `CFrameWnd::RecalcLayout` 。  
  
 MFC 私有 Windows 消息（包括 **WM_SIZEPARENT**）记录在 [技术说明 24](../mfc/tn024-mfc-defined-messages-and-resources.md)中。  
  
## <a name="_mfcnotes_cstatusbar"></a>  CStatusBar  
  
 状态栏是具有一行文本输出窗格的控件条。 使用文本输出窗格的常见方法有两种：  
  
-   作为消息行  
  
     （例如，标准菜单帮助消息行）。 这些通常是通过从 0 开始编制的索引进行访问的  
  
-   作为状态指示器  
  
     （例如，CAP、NUM 和 SCRL 指示器）。 这些一般按字符串/命令 ID 进行访问。  
  
 状态栏的字体为 10 磅 MS Sans Serif（由 Windows 界面应用程序设计指南或与 10 磅非等宽字体最匹配的字体映射程序指定。） 在某些 Windows 版本（如日语版本）上，所选字体不同。  
  
 状态栏使用的颜色还与 Windows 界面应用程序设计指南建议的颜色保持一致。 这些颜色未经过硬编码，将动态更改以响应控制面板中的用户自定义。  
  
|项|Windows 颜色值|默认 RGB|  
|----------|-------------------------|-----------------|  
|状态栏背景|**COLOR_BTNFACE**|RGB(192, 192, 192)|  
|状态栏文本|**COLOR_BTNTEXT**|RGB(000, 000, 000)|  
|状态栏上边缘/左边缘|**COLOR_BTNHIGHLIGHT**|RGB(255, 255, 255)|  
|状态栏下边缘/右边缘|**COLOR_BTNSHADOW**|RGB(128, 128, 128)|  
  
 **CStatusBar 的 CCmdUI 支持**  
  
 指示器一般是通过 `ON_UPDATE_COMMAND_UI` 机制进行更新的。 空闲时，状态栏将调用具有指示器窗格字符串 ID 的 `ON_UPDATE_COMMAND_UI` 处理程序。  
  
 `ON_UPDATE_COMMAND_UI` 处理程序可调用：  
  
- **Enable**：启用或禁用此窗格。 禁用窗格看上去与启用窗格完全一样，但文本不可见（即，禁用了文本指示器）。  
  
- **SetText**：更改文本。 请慎用此设置，因为此窗格不会自动重设大小。  
  
 有关创建 [和自定义 API 的详细信息，请参阅](../mfc/reference/cstatusbar-class.md) 类库参考 *中的* CStatusBar `CStatusBar` 类。 状态栏的大部分自定义应在状态栏最初可见之前完成。  
  
 状态栏仅支持一个伸缩窗格，通常是第一个窗格。 该窗格的大小确实最小。 如果状态栏大于所有窗格的最小大小，则任何多余的宽度都将提供给此伸缩窗格。 由于第一个窗格是伸缩窗格，因此具有状态栏的默认应用程序已与 CAP、NUM 和 SCRL 的指示器右对齐。  
  
## <a name="_mfcnotes_ctoolbar"></a>  CToolBar  
  
 工具栏是具有一行位图按钮（可能包含分隔符）的控件条。 支持两种样式的按钮：按键和复选框按钮。 单选按钮组功能可以使用复选框按钮和 `ON_UPDATE_COMMAND_UI`生成。  
  
 工具栏中的所有位图按钮均来自一个位图。 此位图必须包含每个按钮的一个图像或字形。 通常图像/字形在位图中的顺序与它们在屏幕上绘制的顺序相同。 （这可以使用自定义 API 进行更改。）  
  
 每个按钮的大小必须相同。 默认值为标准的 24x22 像素。 每个图像/字形的大小必须相同，并且必须在位图中并行。 默认图像/字形大小为 16x15 像素。 因此，对于具有 10 个按钮（使用标准大小）的工具栏，您需要一个宽 160 像素、高 15 像素的位图。  
  
 每个按钮都有且只有一个图像/字形。 不同的按钮状态和样式（例如，已按、抬起、按下、已禁用、已禁用并按下、不确定）都是在算法上通过这一个图像/字形生成。 任何颜色位图或 DIB 均可在理论中使用。 如果原始图像是灰色阴影，则生成不同按钮状态的算法最适用。 有关示例，请查看 MFC 常规示例 [CLIPART](../visual-cpp-samples.md) 中提供的标准工具栏按钮和工具栏按钮剪贴画。  
  
 工具栏使用的颜色还与 Windows 界面应用程序设计指南建议的颜色也保持一致。 这些颜色未经过硬编码，将动态更改以响应控制面板中的用户自定义。  
  
|项|Windows 颜色值|默认 RGB|  
|----------|-------------------------|-----------------|  
|工具栏背景|**COLOR_BTNFACE**|RGB(192,192,192)|  
|工具栏按钮上边缘/左边缘|**COLOR_BTNHIGHLIGHT**|RGB(255,255,255)|  
|工具栏按钮下边缘/右边缘|**COLOR_BTNSHADOW**|RGB(128,128,128)|  
  
 此外，将对工具栏位图按钮重新着色，如同它们是标准 Windows 按钮控件一样。 当从资源加载位图时将会进行此重新着色，从而响应“控制面板”中的用户自定义带来的系统颜色的更改。 将自动为工具栏位图中的下列颜色重新着色，因此应慎用这些颜色。 如果您不希望为位图的部分重新着色，则请使用最接近已映射 RGB 值之一的颜色。 映射是基于精确的 RGB 值完成的。  
  
|RGB 值|动态映射的颜色值|  
|---------------|------------------------------------|  
|RGB(000, 000, 000)|COLOR_BTNTEXT|  
|RGB(128, 128, 128)|COLOR_BTNSHADOW|  
|RGB(192, 192, 192)|COLOR_BTNFACE|  
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|  
  
 有关创建 [和自定义 API 的详细信息，请参阅](../mfc/reference/ctoolbar-class.md) 类库参考 *中的* CToolBar `CToolBar` 类。 工具栏的大部分自定义应在工具栏最初可见之前完成。  
  
 自定义 API 可用于调整按钮 ID、样式、分隔线宽度以及什么按钮使用什么图像/字形。 默认情况下不需要使用这些 API。  
  
## <a name="ccmdui-support-for-ctoolbar"></a>CToolBar 的 CCmdUI 支持  
 工具栏按钮始终是通过 `ON_UPDATE_COMMAND_UI` 机制进行更新的。 空闲时，此工具栏将使用按钮的命令 ID 调用 `ON_UPDATE_COMMAND_UI` 处理程序。 将不会为分隔符调用`ON_UPDATE_COMMAND_UI` ，但将为按键和复选框按钮调用此处理程序。  
  
 `ON_UPDATE_COMMAND_UI` 处理程序可调用：  
  
- **Enable**：启用或禁用按钮。 这对按键和复选框按钮同样起作用。  
  
- `SetCheck`：设置按钮的复选状态。 为工具栏按钮调用此会将该按钮转换为复选框按钮。 `SetCheck` 将采用可以为 0（未选中）、1（已选中）或 2（不确定）的参数  
  
- `SetRadio`： `SetCheck`的速记。  
  
 复选框按钮为“自动”复选框按钮；也就是说，如果用户按它们，则它们将立即更改状态。 “已选中”是按下状态。 无内置用户界面方式将按钮更改为“不确定”状态；此操作必须通过代码来完成。  
  
 自定义 API 将允许您更改指定工具栏按钮的状态，您最好针对工具栏按钮代表的命令更改 `ON_UPDATE_COMMAND_UI` 处理程序中的这些状态。 记住，空闲处理将使用 `ON_UPDATE_COMMAND_UI` 处理程序更改工具栏按钮的状态，因此通过 SetButtonStyle 对这些状态所做的任何更改可能在下次空闲后丢失。  
  
 工具栏按钮将像常规按钮或菜单项一样发送 **WM_COMMAND** 消息，并且这些按钮一般将由提供 `ON_COMMAND` 处理程序的同一个类中的 `ON_UPDATE_COMMAND_UI` 处理程序进行处理。  
  
 用于显示状态的工具栏按钮样式（TBBS_ 值）有 4 种：  
  
-   TBBS_CHECKED：   复选框当前处于选中状态（按下）。  
  
-   TBBS_INDETERMINATE：   复选框的状态当前不确定。  
  
-   TBBS_DISABLED：   当前已禁用按钮。  
  
-   TBBS_PRESSED：   当前已按下按钮。  
  
 下列 TBBS 值表示的是 6 种正式的 Windows 界面应用程序设计指南按钮样式：  
  
-   抬起 = 0  
  
-   鼠标按下 = TBBS_PRESSED (&#124;任何其他样式)  
  
-   已禁用 = TBBS_DISABLED  
  
-   按下 = TBBS_CHECKED  
  
-   禁用 = TBBS_CHECKED &#124; TBBS_DISABLED  
  
-   不确定 = TBBS_INDETERMINATE  
  
##  <a name="_mfcnotes_cdialogbar"></a> CDialogBar  
 对话栏是包含标准 Windows 控件的控件条。 其行为类似于一个对话框：它包含控件并且支持使用 Tab 键在控件之间进行切换。 它还使用对话框模板来表示对话栏。  
  
 `CDialogBar` 用于打印预览工具栏，该工具栏包含标准按键控件。  
  
 `CDialogBar` 的用法类似于 `CFormView`。 您必须定义对话栏的对话模框板并移除 **WS_CHILD**之外的所有样式。 请注意，对话框必须是不可见的。  
  
 `CDialogBar` 的控件通知将发送给控件条的父级（如工具栏按钮）。  
  
## <a name="ccmdui-support-for-cdialogbar"></a>CDialogBar 的 CCmdUI 支持  
 对话栏按钮应该通过 `ON_UPDATE_COMMAND_UI` 处理程序机制进行更新。 空闲时，对话栏将调用具有 ID >= 0x8000（即，命令 ID 的范围）的所有按钮的命令 ID 的 `ON_UPDATE_COMMAND_UI` 处理程序。  
  
 `ON_UPDATE_COMMAND_UI` 处理程序可调用：  
  
-   Enable：启用或禁用按钮。  
  
-   SetText：更改按钮的文本。  
  
 自定义可通过标准窗口管理器 API 来完成。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

