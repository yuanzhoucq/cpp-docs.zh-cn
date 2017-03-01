---
title: "CStatusBarCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CStatusBarCtrl
- CStatusBarCtrl class
- status bar controls
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 619fb88b96f60ab2dc0911cb8ea0b66574ea4287
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|创建状态栏控件，并将其附加到`CStatusBarCtrl`对象。|  
|[CStatusBarCtrl::CreateEx](#createex)|创建具有指定的 Windows 扩展样式的状态栏控件并将其附加到`CStatusBarCtrl`对象。|  
|[CStatusBarCtrl::DrawItem](#drawitem)|当所有者描述状态栏控件会发生变化的可视方位时调用。|  
|[CStatusBarCtrl::GetBorders](#getborders)|检索当前的状态栏控件的水平和垂直边框的宽度。|  
|[CStatusBarCtrl::GetIcon](#geticon)|检索当前状态栏控件中的部件 （也称为窗格） 的图标。|  
|[CStatusBarCtrl::GetParts](#getparts)|检索中的状态栏控件的部分数。|  
|[CStatusBarCtrl::GetRect](#getrect)|检索的部分中的状态栏控件的边框。|  
|[CStatusBarCtrl::GetText](#gettext)|检索给定部分的状态栏控件的文本。|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|检索的长度，以字符为单位的状态栏控件的给定部分中的文本。|  
|[Cstatusbarctrl:: Gettiptext](#gettiptext)|检索在状态栏中的窗格中的工具提示文本。|  
|[CStatusBarCtrl::IsSimple](#issimple)|检查状态窗口控件以确定它是否在简单模式中。|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|在状态栏中设置的背景色。|  
|[CStatusBarCtrl::SetIcon](#seticon)|在状态栏中设置一个窗格的图标。|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|条形控件的绘图区域设置状态的最小高度。|  
|[CStatusBarCtrl::SetParts](#setparts)|状态栏控件和每个部分的右边缘的坐标中设置部分的数。|  
|[CStatusBarCtrl::SetSimple](#setsimple)|指定状态栏控件是否显示简单的文本或显示设置的以前调用的所有控件部件`SetParts`。|  
|[CStatusBarCtrl::SetText](#settext)|设置状态栏控件给定部分中的文本。|  
|[Cstatusbarctrl:: Settiptext](#settiptext)|在状态栏中设置一个窗格的工具提示文本。|  
  
## <a name="remarks"></a>备注  
 "状态栏控件"是一个水平窗口，通常显示在父窗口，应用程序可在其中显示各种状态信息的底部。 状态栏控件可以划分成部件以显示多个类型的信息。  
  
 此控件 (并因此`CStatusBarCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 有关详细信息使用`CStatusBarCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-namecreatea--cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl::Create  
 创建状态栏控件，并将其附加到`CStatusBarCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定状态栏控件的样式。 应用状态栏控件样式中列出的任意组合[常见控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此参数必须包括**WS_CHILD**样式。 它还应包括**WS_VISIBLE**样式。  
  
 `rect`  
 指定状态栏控件的大小和位置。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指定控件的父窗口状态栏通常`CDialog`。 它不能**NULL。**  
  
 `nID`  
 指定状态栏控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 您构造`CStatusBarCtrl`分两个步骤。 首先，调用构造函数中，，然后调用**创建**，它创建状态栏控件并将其附加到`CStatusBarCtrl`对象。  
  
 状态窗口的默认位置是父窗口的底部，但您可以指定`CCS_TOP`样式让其显示在父窗口工作区的顶部。 您可以指定**SBARS_SIZEGRIP**样式，包括右端状态窗口的大小调整手柄。 组合`CCS_TOP`和**SBARS_SIZEGRIP**不建议样式，因为生成的大小调整手柄不起作用，即使在状态窗口中的系统绘制它也是如此。  
  
 若要使用扩展的窗口样式创建一个状态栏，调用[CStatusBarCtrl::CreateEx](#createex)而不是**创建**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&1;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="a-namecreateexa--cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CStatusBarCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定状态栏控件的样式。 应用状态栏控件样式中列出的任意组合[常见控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此参数必须包括**WS_CHILD**样式。 它还应包括**WS_VISIBLE**样式。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="a-namecstatusbarctrla--cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl  
 构造 `CStatusBarCtrl` 对象。  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="a-namedrawitema--cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem  
 由框架在所有者绘制状态栏控件会发生变化的可视方位时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向长指针[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构，其中包含有关所需的绘图类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CStatusBarCtrl`对象。  
  
 应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前此成员函数将终止。  
  
##  <a name="a-namegetbordersa--cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarCtrl::GetBorders  
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
 包含三个元素的一个整数数组的地址。 第一个元素收到水平边框的宽度，第二个接收竖框线的宽度，并且第三个收到的矩形之间的边框的宽度。  
  
 *nHorz*  
 对收到水平边框的宽度的整数的引用。  
  
 *转换*  
 对接收竖框线的宽度的整数的引用。  
  
 *nSpacing*  
 对接收的矩形之间的边框宽度的整数的引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 这些界限确定外边缘的控件和控件内包含文本的矩形之间的间距。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&2;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="a-namegeticona--cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarCtrl::GetIcon  
 检索当前状态栏控件中的部件 （也称为窗格） 的图标。  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iPart`|包含要检索的图标部分的从零开始索引。 如果此参数为-1，则假定状态栏是简单模式状态条形图。|  
  
### <a name="return-value"></a>返回值  
 图标的句柄如果成功，则该方法否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 状态栏控件包含实参也称为部件的文本输出窗格的行。 有关状态栏的详细信息，请参阅[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[设置 CStatusBarCtrl 对象的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_statusBar`，也就是说，用来访问当前状态栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将一个图标复制到当前状态栏控件的两个窗格。 如上节的代码示例中我们使用三个窗格创建的状态栏控件，并随后添加到第一个窗格的图标。 此示例检索的第一个窗格的图标，然后将其添加到第二个和第三个窗格中。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="a-namegetpartsa--cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts  
 检索中的状态栏控件的部分数。  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>参数  
 `nParts`  
 要为其检索坐标的部分数。 如果此参数为大于该控件中的部分数，消息会检索现有的部件的坐标。  
  
 *pParts*  
 整数数组具有相同数量的元素作为包含几个部分由指定的地址`nParts`。 数组中的每个元素接收的相应部分的右边缘的客户端坐标。 如果元素设置为-1，该部分的右边缘的位置会延伸到状态栏的右边缘。  
  
### <a name="return-value"></a>返回值  
 如果成功，该控件或为零; 否则为中的部分数。  
  
### <a name="remarks"></a>备注  
 此成员函数还将检索给定的部分数的右边缘的坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&3;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="a-namegetrecta--cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect  
 检索的部分中的状态栏控件的边框。  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPane`  
 其边框是要检索的部分的从零开始索引。  
  
 `lpRect`  
 地址的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它接收的边框。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&4;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="a-namegettexta--cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarCtrl::GetText  
 检索给定部分的状态栏控件的文本。  
  
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
 `lpszText`  
 接收的文本的缓冲区地址。 此参数是以 null 结尾的字符串。  
  
 `nPane`  
 要从中检索文本部分从零开始索引。  
  
 `pType`  
 指向一个整数，它接收的类型信息。 类型可以是下列值之一︰  
  
- **0**具有边框显示低于状态栏的平面绘制文本。  
  
- `SBT_NOBORDERS`没有边框的情况下绘制文本。  
  
- `SBT_POPOUT`使用边框来显示高于状态栏的平面绘制文本。  
  
- `SBT_OWNERDRAW`如果文本`SBT_OWNERDRAW`绘图类型，`pType`接收此消息，并返回与文本而不是长度和操作类型相关联的 32 位值。  
  
### <a name="return-value"></a>返回值  
 长度，以字符为单位的文本或[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含当前文本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&5;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="a-namegettextlengtha--cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarCtrl::GetTextLength  
 检索的长度，以字符为单位的状态栏控件的给定部分中的文本。  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPane`  
 要从中检索文本部分从零开始索引。  
  
 `pType`  
 指向一个整数，它接收的类型信息。 类型可以是下列值之一︰  
  
- **0**具有边框显示低于状态栏的平面绘制文本。  
  
- `SBT_NOBORDERS`没有边框的情况下绘制文本。  
  
- `SBT_OWNERDRAW`通过父窗口中绘制文本。  
  
- `SBT_POPOUT`使用边框来显示高于状态栏的平面绘制文本。  
  
### <a name="return-value"></a>返回值  
 长度 （以字符为单位的文本）。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&6;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="a-namegettiptexta--cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>Cstatusbarctrl:: Gettiptext  
 检索在状态栏中的窗格中的工具提示文本。  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPane`  
 状态栏窗格来接收工具提示文本的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含的工具提示中使用的文本。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&7;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="a-nameissimplea--cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarCtrl::IsSimple  
 检查状态窗口控件以确定它是否在简单模式中。  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果状态窗口控件在简单模式，则为非零值否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetbkcolora--cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor  
 在状态栏中设置的背景色。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 **COLORREF**值，该值指定新的背景色。 指定`CLR_DEFAULT`值以使状态栏，使用它的默认背景色。  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值表示以前的默认背景色。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&8;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="a-nameseticona--cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarCtrl::SetIcon  
 在状态栏中设置一个窗格的图标。  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 `nPane`  
 将接收该图标在窗格的从零开始的索引。 如果此参数为-1，则假定状态栏是一个简单的状态栏。  
  
 `hIcon`  
 要设置的图标的句柄。 如果此值为**NULL**，图标会从该部件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CStatusBarCtrl::SetBkColor](#setbkcolor)。  
  
##  <a name="a-namesetminheighta--cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight  
 条形控件的绘图区域设置状态的最小高度。  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 以像素为单位，该控件的最小高度。  
  
### <a name="remarks"></a>备注  
 最小高度均`nMin`和两次的宽度，以像素为单位，状态栏控件的垂直边框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&9;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="a-namesetpartsa--cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarCtrl::SetParts  
 状态栏控件和每个部分的右边缘的坐标中设置部分的数。  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>参数  
 `nParts`  
 若要设置的部分数。 包含几个部分不能大于 255。  
  
 *pWidths*  
 整数数组具有相同数量的元素作为部件由指定的地址`nParts`。 数组中的每个元素指定的相应部分的右边缘的位置，在工作区坐标。 如果元素为 – 1，该部分的右边缘的位置将扩展到该控件的右边缘。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&10;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="a-namesetsimplea--cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarCtrl::SetSimple  
 指定状态栏控件是否显示简单的文本或显示设置的以前调用的所有控件部件[SetParts](#setparts)。  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSimple`  
 显示类型的标志。 如果此参数为`TRUE`，该控件显示简单的文本; 如果它是`FALSE`，它将显示多个部分。  
  
### <a name="return-value"></a>返回值  
 始终返回 0。  
  
### <a name="remarks"></a>备注  
 如果为 simple 时，反之亦然，您的应用程序从非简单更改状态栏控件，系统将立即重绘控件。  
  
##  <a name="a-namesettexta--cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarCtrl::SetText  
 设置状态栏控件给定部分中的文本。  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 用于指定要设置的文本且以 Null 结尾的字符串的地址。 如果 `nType` 为 `SBT_OWNERDRAW`，则 `lpszText` 表示 32 位的数据。  
  
 `nPane`  
 要设置部件的从零开始的索引。 如果此值为 255，则假定状态栏控件是仅具有一个部件的简单控件。  
  
 `nType`  
 绘制操作的类型。 请参阅[SB_SETTEXT 消息](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx)有关的可能值列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 该消息会使已更改的控件部分失效，从而导致该控件在下一个控件收到 `WM_PAINT` 消息时显示新文本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&11;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="a-namesettiptexta--cstatusbarctrlsettiptext"></a><a name="settiptext"></a>Cstatusbarctrl:: Settiptext  
 在状态栏中设置一个窗格的工具提示文本。  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>参数  
 `nPane`  
 状态栏窗格来接收工具提示文本的从零开始的索引。  
  
 *pszTipText*  
 指向包含的工具提示文本的字符串的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&12;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)

