---
title: CStatusBarCtrl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b89f51fbcb3ca46afdb5ad56a6e162e7fe42cf0d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122884"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 类
提供 Windows 公共状态栏控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|构造 `CStatusBarCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|创建状态栏控件并将其附加到`CStatusBarCtrl`对象。|  
|[CStatusBarCtrl::CreateEx](#createex)|创建指定的 Windows 扩展样式状态栏控件，并将其附加到`CStatusBarCtrl`对象。|  
|[CStatusBarCtrl::DrawItem](#drawitem)|当所有者描述状态栏控件会发生变化的可视方面时调用。|  
|[CStatusBarCtrl::GetBorders](#getborders)|检索当前状态栏控件的水平和垂直边框的宽度。|  
|[CStatusBarCtrl::GetIcon](#geticon)|检索当前状态栏控件中的一部分 （也称为窗格） 的图标。|  
|[CStatusBarCtrl::GetParts](#getparts)|检索状态栏控件中的部件的计数。|  
|[CStatusBarCtrl::GetRect](#getrect)|检索参与状态栏控件的边框。|  
|[Cstatusbarctrl:: Gettext](#gettext)|从状态栏控件给定部分中检索文本。|  
|[Cstatusbarctrl:: Gettextlength](#gettextlength)|检索的长度，以字符为单位的状态栏控件给定部分中的文本。|  
|[Cstatusbarctrl:: Gettiptext](#gettiptext)|检索在状态栏中显示窗格的工具提示文本。|  
|[CStatusBarCtrl::IsSimple](#issimple)|检查以确定它是否在简单的模式下状态窗口控件。|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|在状态栏中设置的背景色。|  
|[CStatusBarCtrl::SetIcon](#seticon)|在状态栏中设置窗格中的图标。|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|栏控件的绘图区域设置状态的最小高度。|  
|[CStatusBarCtrl::SetParts](#setparts)|状态栏控件和每个部分的右边缘的坐标中设置部分的数。|  
|[CStatusBarCtrl::SetSimple](#setsimple)|指定状态栏控件显示简单文本还是显示所有设置的以前调用的控件部件`SetParts`。|  
|[CStatusBarCtrl::SetText](#settext)|设置状态栏控件给定部分中的文本。|  
|[Cstatusbarctrl:: Settiptext](#settiptext)|在状态栏中设置窗格中的工具提示文本。|  
  
## <a name="remarks"></a>备注  
 "状态栏控件"是一个水平的窗口，通常显示在父窗口，应用程序可在其中显示各种状态信息的底部。 状态栏控件可以划分为部件以显示多个类型的信息。  
  
 此控件 (因此`CStatusBarCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 有关详细信息使用`CStatusBarCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="create"></a>  CStatusBarCtrl::Create  
 创建状态栏控件并将其附加到`CStatusBarCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *dwStyle*  
 指定状态栏控件的样式。 应用状态栏控件样式中列出的任意组合[公共控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)Windows SDK 中。 此参数必须包含 WS_CHILD 样式。 它还应包括 WS_VISIBLE 样式。  
  
 *rect*  
 指定状态栏控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 *pParentWnd*  
 通常指定控件的父窗口状态栏`CDialog`。 不得为 NULL。  
  
 *nID*  
 指定状态栏控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 构造`CStatusBarCtrl`中两个步骤。 首先，调用的构造函数，然后调用`Create`，它创建状态栏控件并将其附加到`CStatusBarCtrl`对象。  
  
 状态窗口的默认位置为父窗口的底部，但您可以指定 CCS_TOP 样式让其显示在父窗口工作区的顶部。 你可以指定要包括在状态窗口的右端大小调整手柄的 SBARS_SIZEGRIP 样式。 不建议结合 CCS_TOP 和 SBARS_SIZEGRIP 样式，因为生成的大小调整手柄不起作用，即使系统将其绘制在状态窗口中也是如此。  
  
 若要创建具有扩展的窗口样式状态栏，请调用[CStatusBarCtrl::CreateEx](#createex)而不是`Create`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CStatusBarCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CStatusBarCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *dwExStyle*  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 *dwStyle*  
 指定状态栏控件的样式。 应用状态栏控件样式中列出的任意组合[公共控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)Windows SDK 中。 此参数必须包含 WS_CHILD 样式。 它还应包括 WS_VISIBLE 样式。  
  
 *rect*  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置*pParentWnd*。  
  
 *pParentWnd*  
 指向控件的父级的窗口的指针。  
  
 *nID*  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl  
 构造 `CStatusBarCtrl` 对象。  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem  
 由框架在所有者绘制状态栏控件会发生变化的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 *lpDrawItemStruct*  
 指向的长指针[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构，其中包含有关所需的绘图的类型的信息。  
  
### <a name="remarks"></a>备注  
 `itemAction`的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CStatusBarCtrl`对象。  
  
 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象*lpDrawItemStruct*之前此成员函数将终止。  
  
##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders  
 检索状态栏控件的当前宽度的水平和垂直边框和矩形之间的空间。  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>参数  
 *pBorders*  
 整数数组具有三个元素的地址。 第一个元素收到水平边框的宽度、 第二个接收的垂直边框的宽度和第三个接收的矩形之间的边框的宽度。  
  
 *nHorz*  
 对一个整数，它接收横框线的宽度的引用。  
  
 *转换*  
 对一个整数，它接收竖框线的宽度的引用。  
  
 *nSpacing*  
 对一个整数，它接收矩形之间的边框的宽度的引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 这些边框确定控件的外部边缘和包含文本控件内的矩形之间的间距。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon  
 检索当前状态栏控件中的一部分 （也称为窗格） 的图标。  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iPart*|包含要检索的图标部分的从零开始索引。 如果此参数为-1，则假定状态栏是一个简单的模式状态条形图。|  
  
### <a name="return-value"></a>返回值  
 图标的句柄如果成功，则该方法否则，为 NULL。  
  
### <a name="remarks"></a>备注  
 此方法可发送[SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744)消息，Windows SDK 中介绍。  
  
 状态栏控件包含文本输出窗格，它们是也称为部分的行。 有关状态栏的详细信息，请参阅[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[设置 CStatusBarCtrl 对象的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_statusBar`，即用于访问当前状态栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将复制到当前状态栏控件的两个窗格的一个图标。 如上节的代码示例中我们使用三个窗格创建状态栏控件，并随后添加到的第一个窗格的图标。 此示例从第一个窗格检索图标，然后将其添加到第二个和第三个窗格。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>  CStatusBarCtrl::GetParts  
 检索状态栏控件中的部件的计数。  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>参数  
 *nParts*  
 为其检索坐标的部分数。 如果此参数为大于控件中的各部分的数量，消息会检索仅现有部件的坐标。  
  
 *pParts*  
 整数数组的指定的部分数为具有相同数量的元素的地址*nParts*。 数组中的每个元素接收的相应部分的右边缘的客户端坐标。 如果元素设置为-1，该部分的右边缘的位置扩展状态栏的右边缘。  
  
### <a name="return-value"></a>返回值  
 如果成功，该控件或零否则为中的部分数。  
  
### <a name="remarks"></a>备注  
 此成员函数还将检索的部分给定数的右边缘的坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>  CStatusBarCtrl::GetRect  
 检索参与状态栏控件的边框。  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 *nPane*  
 其边界的矩形是要检索的部分的从零开始索引。  
  
 *lpRect*  
 地址[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它接收的边框。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>  Cstatusbarctrl:: Gettext  
 从状态栏控件给定部分中检索文本。  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpszText*  
 接收的文本的缓冲区的地址。 此参数是以 null 结尾的字符串。  
  
 *nPane*  
 要从中检索文本部分从零开始索引。  
  
 *pType*  
 指向一个整数，它接收的类型信息。 类型可以是下列值之一：  
  
- **0**有一个边框，显示低于状态栏的平面绘制文本。  
  
- SBT_NOBORDERS 没有边框绘制文本。  
  
- SBT_POPOUT 文本中进行绘制，边框来显示高于状态栏的平面。  
  
- SBT_OWNERDRAW 文本是否绘制类型，SBT_OWNERDRAW *pType*接收此消息，并返回与文本而不是长度和操作类型关联的 32 位值。  
  
### <a name="return-value"></a>返回值  
 长度，以字符为单位的文本或[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含当前的文本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>  Cstatusbarctrl:: Gettextlength  
 检索的长度，以字符为单位的状态栏控件给定部分中的文本。  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *nPane*  
 要从中检索文本部分从零开始索引。  
  
 *pType*  
 指向一个整数，它接收的类型信息。 类型可以是下列值之一：  
  
- **0**有一个边框，显示低于状态栏的平面绘制文本。  
  
- SBT_NOBORDERS 没有边框绘制文本。  
  
- SBT_OWNERDRAW 由父窗口中绘制文本。  
  
- SBT_POPOUT 文本中进行绘制，边框来显示高于状态栏的平面。  
  
### <a name="return-value"></a>返回值  
 以字符为单位，文本的长度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>  Cstatusbarctrl:: Gettiptext  
 检索在状态栏中显示窗格的工具提示文本。  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>参数  
 *nPane*  
 状态栏窗格以接收的工具提示文本的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要在工具提示中使用的文本。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple  
 检查以确定它是否在简单的模式下状态窗口控件。  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果状态窗口控件处于简单模式，则为非零否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753)，如 Windows SDK 中所述。  
  
##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor  
 在状态栏中设置的背景色。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 *cr*  
 COLORREF 值，该值指定新的背景色。 指定要导致状态栏以使用其默认背景色的 CLR_DEFAULT 值。  
  
### <a name="return-value"></a>返回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值表示的以前的默认背景色。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon  
 在状态栏中设置窗格中的图标。  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 *nPane*  
 将接收图标的窗格中的从零开始的索引。 如果此参数为-1，则假定状态栏是一个简单的状态条形图。  
  
 *任务栏*  
 要设置的图标的句柄。 如果此值为 NULL，图标将从该部件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
  请参阅示例[CStatusBarCtrl::SetBkColor](#setbkcolor)。  
  
##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight  
 栏控件的绘图区域设置状态的最小高度。  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>参数  
 *nMin*  
 以像素为单位，该控件的最小高度。  
  
### <a name="remarks"></a>备注  
 最小高度之*nMin*和两次的宽度，以像素为单位，状态栏控件的垂直边框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>  CStatusBarCtrl::SetParts  
 状态栏控件和每个部分的右边缘的坐标中设置部分的数。  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>参数  
 *nParts*  
 若要设置的部分数。 部件数不能大于 255。  
  
 *pWidths*  
 整数数组具有相同数量的元素作为部件由指定的地址*nParts*。 数组中的每个元素指定相应的部件的右边缘的位置，在工作区坐标。 如果元素是-1，该部分的右边缘的位置扩展控件的右边缘。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple  
 指定状态栏控件显示简单文本还是显示所有设置的以前调用的控件部件[SetParts](#setparts)。  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bSimple*  
 显示类型标志。 如果此参数为 TRUE，控件将显示简单的文本;如果它为 FALSE，则会显示多个部分。  
  
### <a name="return-value"></a>返回值  
 始终返回 0。  
  
### <a name="remarks"></a>备注  
 如果为 simple 时，反之亦然，你的应用程序从非简单更改状态栏控件，系统将立即重绘控件。  
  
##  <a name="settext"></a>  CStatusBarCtrl::SetText  
 设置状态栏控件给定部分中的文本。  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>参数  
 *lpszText*  
 用于指定要设置的文本且以 Null 结尾的字符串的地址。 如果*nType*是 SBT_OWNERDRAW， *lpszText*表示 32 位的数据。  
  
 *nPane*  
 要设置部件的从零开始的索引。 如果此值为 255，则假定状态栏控件是仅具有一个部件的简单控件。  
  
 *nType*  
 绘制操作的类型。 请参阅[SB_SETTEXT 消息](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx)有关可能的值的列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 消息将使已更改，从而导致该控件在下一步收到 WM_PAINT 消息时显示新的文本的控件部分失效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>  Cstatusbarctrl:: Settiptext  
 在状态栏中设置窗格中的工具提示文本。  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>参数  
 *nPane*  
 状态栏窗格以接收的工具提示文本的从零开始的索引。  
  
 *pszTipText*  
 指向包含的工具提示文本的字符串的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)
