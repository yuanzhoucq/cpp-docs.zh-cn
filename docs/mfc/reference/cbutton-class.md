---
title: "CButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
dev_langs:
- C++
helpviewer_keywords:
- CButton class
- checkbox buttons
- pushbuttons
- button control [MFC]
- check boxes, button controls
- button objects (CButton)
- radio buttons, CButton class
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: 19
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
ms.openlocfilehash: 751d4aee2c734acd455734ca694eb88bb149fc09
ms.lasthandoff: 02/24/2017

---
# <a name="cbutton-class"></a>CButton 类
提供 Windows 按钮控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CButton : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CButton::CButton](#cbutton)|构造 `CButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CButton::Create](#create)|创建的 Windows 按钮控件并将其附加到`CButton`对象。|  
|[CButton::DrawItem](#drawitem)|若要绘制一个所有者绘制的替代`CButton`对象。|  
|[CButton::GetBitmap](#getbitmap)|检索与以前设置的位图的句柄[SetBitmap](#setbitmap)。|  
|[CButton::GetButtonStyle](#getbuttonstyle)|检索有关按钮控件样式信息。|  
|[CButton::GetCheck](#getcheck)|检索一个 button 控件的复选状态。|  
|[CButton::GetCursor](#getcursor)|检索与以前设置的光标图像的句柄[SetCursor](#setcursor)。|  
|[CButton::GetIcon](#geticon)|检索与以前设置的图标的句柄[SetIcon](#seticon)。|  
|[CButton::GetIdealSize](#getidealsize)|检索按钮控件的理想大小。|  
|[CButton::GetImageList](#getimagelist)|检索按钮控件的图像列表。|  
|[CButton::GetNote](#getnote)|检索当前命令链接控件的注意组件。|  
|[CButton::GetNoteLength](#getnotelength)|检索当前 command link 控件的注释文本的长度。|  
|[CButton::GetSplitGlyph](#getsplitglyph)|检索与当前的拆分按钮控件关联的标志符号。|  
|[CButton::GetSplitImageList](#getsplitimagelist)|检索当前的拆分按钮控件的图像列表。|  
|[CButton::GetSplitInfo](#getsplitinfo)|检索定义当前拆分按钮控件的信息。|  
|[CButton::GetSplitSize](#getsplitsize)|检索当前的拆分按钮控件的下拉部分的边框。|  
|[CButton::GetSplitStyle](#getsplitstyle)|检索定义当前拆分按钮控件的拆分按钮样式。|  
|[CButton::GetState](#getstate)|检索检查状态、 突出显示状态和按钮控件的焦点状态。|  
|[CButton::GetTextMargin](#gettextmargin)|检索按钮控件的文本边距。|  
|[CButton::SetBitmap](#setbitmap)|指定该按钮上显示的位图。|  
|[CButton::SetButtonStyle](#setbuttonstyle)|更改按钮的样式。|  
|[CButton::SetCheck](#setcheck)|设置按钮控件的复选状态。|  
|[CButton::SetCursor](#setcursor)|指定要在按钮上显示的光标图像。|  
|[CButton::SetDropDownState](#setdropdownstate)|设置当前的拆分按钮控件的下拉列表状态。|  
|[CButton::SetIcon](#seticon)|指定要在按钮上显示的图标。|  
|[CButton::SetImageList](#setimagelist)|设置按钮控件的图像列表。|  
|[CButton::SetNote](#setnote)|当前命令链接控件上设置了说明。|  
|[CButton::SetSplitGlyph](#setsplitglyph)|将指定的标志符号与当前的拆分按钮控件相关联。|  
|[CButton::SetSplitImageList](#setsplitimagelist)|将图像列表与当前的拆分按钮控件相关联。|  
|[CButton::SetSplitInfo](#setsplitinfo)|指定定义当前拆分按钮控件的信息。|  
|[CButton::SetSplitSize](#setsplitsize)|设置当前的拆分按钮控件的下拉部分的边框。|  
|[CButton::SetSplitStyle](#setsplitstyle)|设置当前的拆分按钮控件的样式。|  
|[CButton::SetState](#setstate)|设置按钮控件的突出显示状态。|  
|[CButton::SetTextMargin](#settextmargin)|设置按钮控件的文本边距。|  
  
## <a name="remarks"></a>备注  
 按钮控件是可以通过单击打开和关闭的小，为矩形子窗口。 按钮可单独使用或在组中，并且可以进行标记或不包含文本会显示。 当用户单击它时，一个按钮通常会更改外观。  
  
 典型的按钮是复选框、 单选按钮和按钮。 一个`CButton`对象都能成为上述，任何符合[按钮样式](../../mfc/reference/button-styles.md)在由其初始化时指定[创建](#create)成员函数。  
  
 此外， [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)类派生自`CButton`支持创建使用位图图像而非文本进行标记的按钮控件。 一个`CBitmapButton`可以具有单独的位图，为一个按钮将的、 向下、 向中心，且禁用状态。  
  
 从对话框模板或直接在代码中，可以创建一个按钮控件。 在这两种情况下，第一次调用构造函数`CButton`构造`CButton`对象; 然后，调用**创建**成员函数来创建 Windows 按钮控件，然后将其附加到`CButton`对象。  
  
 构造可能是在派生类中的单步进程`CButton`。 编写构造函数以及该派生的类调用**创建**从构造函数内。  
  
 如果你想要处理 Windows 通知消息发送到其父级的按钮控件 (通常派生自该类[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每个消息的父类。  
  
 每个消息映射条目采用以下形式︰  
  
 **ON_**Notification **(**`id`, `memberFxn`**)**  
  
 其中`id`指定发送通知的控件的子窗口 ID 和`memberFxn`留下来处理通知的父成员函数的名称。  
  
 父元素的函数原型是，如下所示︰  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 潜在的消息映射条目如下所示︰  
  
|映射条目|发送至父项时...|  
|---------------|----------------------------|  
|**ON_BN_CLICKED**|用户单击按钮。|  
|**ON_BN_DOUBLECLICKED**|用户双击按钮。|  
  
 如果您创建`CButton`对话框资源，从对象`CButton`当用户关闭对话框中，将自动销毁对象。  
  
 如果您创建`CButton`对象在窗口中，您可能需要将其销毁。 如果您创建`CButton`使用堆上的对象**新**函数，则必须调用**删除**对象以将其销毁，当用户关闭 Windows 按钮控件。 如果您创建`CButton`在堆栈上，或它的对象嵌入父对象中的对话框中，自动被销毁。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cbutton"></a>CButton::CButton  
 构造 `CButton` 对象。  
  
```  
CButton();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&1;](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>CButton::Create  
 创建的 Windows 按钮控件并将其附加到`CButton`对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `lpszCaption`  
 指定按钮控件的文本。  
  
 `dwStyle`  
 指定按钮控件的样式。 应用的任意组合[按钮样式](../../mfc/reference/button-styles.md)到按钮。  
  
 `rect`  
 指定按钮控件的大小和位置。 它可为`CRect`对象或`RECT`结构。  
  
 `pParentWnd`  
 指定按钮控件的父窗口，通常`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定按钮控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CButton`在两个步骤中的对象。 首先，调用构造函数，然后调用**创建**，它创建的 Windows 按钮控件并将其附加到`CButton`对象。  
  
 如果**WS_VISIBLE**提供样式，Windows 将按钮控件发送了激活和显示按钮所需的所有消息。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)到按钮控件︰  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**控件组合  
  
- **WS_TABSTOP**要包括在 tab 键顺序中的按钮  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&2;](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>CButton::DrawItem  
 当所有者描述的按钮的可视特征发生更改时由框架调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向长指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构。 该结构包含有关要绘制的项和绘图所需的类型信息。  
  
### <a name="remarks"></a>备注  
 所有者描述的按钮具有**BS_OWNERDRAW**样式集。 重写该成员函数以实现绘制一个所有者绘制的`CButton`对象。 应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前该成员函数将终止。  
  
 另请参阅[BS_](../../mfc/reference/button-styles.md)的样式值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&3;](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>CButton::GetBitmap  
 调用此成员函数以获取与以前设置的位图的句柄[SetBitmap](#setbitmap)，即与按钮相关联。  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向位图的句柄。 **NULL**当以前指定不使用位图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&4;](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>CButton::GetButtonStyle  
 检索有关按钮控件样式信息。  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回此按钮样式`CButton`对象。 此函数仅返回[BS_](../../mfc/reference/button-styles.md)样式值，不是任何其他窗口样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&5;](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>CButton::GetCheck  
 检索单选按钮或复选框的选中状态。  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>返回值  
 使用创建的按钮控件的返回值**BS_AUTOCHECKBOX**， **BS_AUTORADIOBUTTON**， **BS_AUTO3STATE**， **BS_CHECKBOX**， **BS_RADIOBUTTON**，或**BS_3STATE**样式是下列值之一︰  
  
|值|含义|  
|-----------|-------------|  
|**BST_UNCHECKED**|按钮状态没有被选中。|  
|**BST_CHECKED**|按钮状态进行检查。|  
|**BST_INDETERMINATE**|按钮状态是不确定的 (仅适用于该按钮具有**BS_3STATE**或**BS_AUTO3STATE**样式)。|  
  
 如果该按钮具有任何其他样式，返回值是**BST_UNCHECKED**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&6;](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>CButton::GetCursor  
 调用此成员函数可获取与以前设置光标的句柄[SetCursor](#setcursor)，即与按钮相关联。  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>返回值  
 光标图像句柄。 **NULL**当以前指定无游标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&7;](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>CButton::GetIcon  
 调用此成员函数可获取与以前设置的图标的句柄[SetIcon](#seticon)，即与按钮相关联。  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向一个图标的句柄。 **NULL**当以前指定无图标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&8;](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CButton::GetIdealSize  
 检索按钮控件的理想大小。  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>参数  
 *psize*  
 指向按钮的当前大小的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_GETIDEALSIZE**消息，如中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)部分[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getimagelist"></a>CButton::GetImageList  
 调用此方法以获取从按钮控件的图像列表。  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>参数  
 `pbuttonImagelist`  
 指向的指针的图像列表`CButton`对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_GETIMAGELIST**消息，如中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)部分[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getnote"></a>CButton::GetNote  
 检索与当前的 command link 控件相关联的注释文本。  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `lpszNote`|指向调用方负责分配和解除分配的缓冲区的指针。 如果返回值是`true`，在缓冲区中包含注释文本与当前的 command link 控件相关联; 否则为，缓冲区保持不变。|  
|[in, out] `cchNote`|无符号的整数变量的指针。<br /><br /> 当调用此方法时，该变量包含指定的缓冲区的大小`lpszNote`参数。<br /><br /> 此方法返回时，如果返回值是`true`变量包含与当前命令链接控件相关联的注释的大小。 如果返回值是`false`，该变量包含包含注释所需的缓冲区大小。|  
  
### <a name="return-value"></a>返回值  
 在第一个重载中， [CString](../../atl-mfc-shared/using-cstring.md)对象，其中包含与当前的 command link 控件相关联的注释文本。  
  
 - 或 -  
  
 在第二个重载中，`true`此方法成功，否则为如果`false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_COMMANDLINK`或`BS_DEFCOMMANDLINK`。  
  
 此方法可发送[BCM_GETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775965)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getnotelength"></a>CButton::GetNoteLength  
 检索当前 command link 控件的注释文本的长度。  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 16 位 Unicode 字符，用于当前命令链接控件中的备注文本的长度。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_COMMANDLINK`或`BS_DEFCOMMANDLINK`。  
  
 此方法可发送[BCM_GETNOTELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb775967)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getsplitglyph"></a>CButton::GetSplitGlyph  
 检索与当前的拆分按钮控件关联的标志符号。  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>返回值  
 与当前的拆分按钮控件关联的标志符号字符。  
  
### <a name="remarks"></a>备注  
 一个标志符号是特定字体中字符的物理表示。 例如，可能会具有复选标记的 Unicode 字符的字形修饰拆分按钮控件 (U +&2713;)。  
  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_GLYPH`标志，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当消息函数返回时，此方法检索从标志符号`himlGlyph`结构中的成员。  
  
##  <a name="getsplitimagelist"></a>CButton::GetSplitImageList  
 检索[图像列表](../../mfc/reference/cimagelist-class.md)当前拆分按钮控件。  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_IMAGE`标志，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当消息函数返回时，此方法检索从图像列表`himlGlyph`结构中的成员。  
  
##  <a name="getsplitinfo"></a>CButton::GetSplitInfo  
 检索参数，以确定 Windows 如何绘制当前拆分按钮控件。  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pInfo`|指向[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)接收当前拆分按钮控件的相关信息的结构。 调用方负责分配结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法可发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getsplitsize"></a>CButton::GetSplitSize  
 检索当前的拆分按钮控件的下拉部分的边框。  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pSize`|指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，它接收的矩形的说明。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 当扩展拆分按钮控件时，它可以显示下拉菜单的组件，如页导航控件或列表控件。 此方法检索包含下拉列表组件的边框。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_SIZE`标志，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当消息函数返回时，此方法检索从边框`size`结构中的成员。  
  
##  <a name="getsplitstyle"></a>CButton::GetSplitStyle  
 检索定义当前拆分按钮控件的拆分按钮样式。  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 拆分按钮样式按位组合。 有关详细信息，请参阅`uSplitStyle`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 拆分按钮样式指定的对齐方式、 纵横比和图形格式与 Windows 绘制拆分按钮图标。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_STYLE`标志，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当消息函数返回时，此方法检索中的拆分按钮样式`uSplitStyle`结构中的成员。  
  
##  <a name="getstate"></a>CButton::GetState  
 检索一个 button 控件的状态。  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含的值，用于指示按钮控件的当前状态组合一个位域。 下表列出可能的值。  
  
|按钮状态|值|说明|  
|------------------|-----------|-----------------|  
|`BST_UNCHECKED`|0x0000|初始状态。|  
|`BST_CHECKED`|它需要&0;x0001|Button 控件进行检查。|  
|`BST_INDETERMINATE`|0x0002|状态是不确定 （才可能出现在按钮在控件有以下三种状态时）。|  
|`BST_PUSHED`|0x0004|按下按钮控件。|  
|`BST_FOCUS`|0x0008|Button 控件具有焦点。|  
  
### <a name="remarks"></a>备注  
 使用一个按钮控件`BS_3STATE`或`BS_AUTO3STATE`按钮样式创建一个具有名为不确定状态的第三个状态的复选框。 不确定状态表示此复选框处于选中和取消选中都不。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&9;](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>CButton::GetTextMargin  
 调用此方法以获取文本的页边空白处`CButton`对象。  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>参数  
 `pmargin`  
 一个指向文本的页边空白处`CButton`对象。  
  
### <a name="return-value"></a>返回值  
 返回文本边距。  
  
### <a name="remarks"></a>备注  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_GETTEXTMARGIN**消息，如中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)部分[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setbitmap"></a>CButton::SetBitmap  
 调用该成员函数以将新位图与按钮相关联。  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 位图的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与该按钮关联的位图的句柄。  
  
### <a name="remarks"></a>备注  
 位图将被自动放置按钮，以默认情况下为中心的表面上。 如果位图按钮太大，则将任意一侧剪辑元素。 您可以选择其他对齐选项，其中包括︰  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 与不同[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它使用每个按钮，四个位图`SetBitmap`使用每个按钮只能有一个位图。 按下了按钮，该位图看起来会向下和向右移动。  
  
 您有责任在完成时将其释放位图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&4;](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>CButton::SetButtonStyle  
 更改按钮的样式。  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nStyle`  
 指定[按钮样式](../../mfc/reference/button-styles.md)。  
  
 `bRedraw`  
 指定是否要重新绘制按钮。 一个非零值重绘按钮。 值 0 不会刷新按钮。 默认情况下，重绘按钮。  
  
### <a name="remarks"></a>备注  
 使用`GetButtonStyle`成员函数以检索按钮样式。 完成按钮样式的低位字是特定于按钮的样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&5;](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>CButton::SetCheck  
 设置或重置的复选状态的单选按钮或复选框。  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>参数  
 `nCheck`  
 指定的复选状态。 此参数可以是以下项之一︰  
  
|值|含义|  
|-----------|-------------|  
|**BST_UNCHECKED**|按钮状态设置为未选中。|  
|**BST_CHECKED**|设置按钮的状态检查。|  
|**BST_INDETERMINATE**|按钮状态设置为不确定。 可以使用此值，仅当该按钮具有**BS_3STATE**或**BS_AUTO3STATE**样式。|  
  
### <a name="remarks"></a>备注  
 此成员函数具有对某个按钮没有影响。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&6;](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>CButton::SetCursor  
 调用该成员函数以将新光标与按钮相关联。  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>参数  
 `hCursor`  
 光标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与该按钮关联的游标的句柄。  
  
### <a name="remarks"></a>备注  
 光标将自动放置按钮，以默认情况下为中心的表面上。 如果光标位于按钮太大，则将任意一侧剪辑元素。 您可以选择其他对齐选项，其中包括︰  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 与不同[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它使用每个按钮，四个位图`SetCursor`使用每个按钮只能有一个游标。 按下了按钮，将显示光标向下和向右移动。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&7;](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>CButton::SetDropDownState  
 设置当前的拆分按钮控件的下拉列表状态。  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `fDropDown`|`true`若要设置`BST_DROPDOWNPUSHED`状态; 否则为`false`。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 拆分按钮控件具有一种样式的`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`，组成一个按钮以及指向其右侧的下拉箭头。 有关详细信息，请参阅[按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)。 通常情况下，当用户单击下拉箭头设置下拉列表状态。 使用此方法以编程方式设置该控件的下拉列表状态。 下拉箭头将绘制阴影，以指示的状态。  
  
 此方法可发送[BCM_SETDROPDOWNSTATE](http://msdn.microsoft.com/library/windows/desktop/bb775973)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，也就是说，用来以编程方式访问拆分按钮控件。 在下面的示例使用该变量。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置拆分按钮控件，以指示推送下拉箭头的状态。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&6;](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>CButton::SetElevationRequired  
 设置为当前的按钮控件的状态`elevation required`，这是必需的控件以显示一个提升的安全图标。  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `fElevationRequired`|`true`若要设置`elevation required`状态; 否则为`false`。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果一个按钮或命令链接控件需要提升权限的安全权限来执行某项操作，请将控件设置为`elevation required`状态。 随后，Windows 将显示用户帐户控制 (UAC) 盾牌图标在控件上。 有关详细信息，查看"用户帐户控制" [MSDN](http://go.microsoft.com/fwlink/linkid=18507)。  
  
 此方法可发送[BCM_SETSHIELD](http://msdn.microsoft.com/library/windows/desktop/bb775979)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="seticon"></a>CButton::SetIcon  
 调用该成员函数以将新建图标的按钮相关联。  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 `hIcon`  
 图标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与该按钮关联的图标的句柄。  
  
### <a name="remarks"></a>备注  
 该图标将自动放置按钮，以默认情况下为中心的表面上。 如果图标的按钮太大，则将任意一侧剪辑元素。 您可以选择其他对齐选项，其中包括︰  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 与不同[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它使用每个按钮，四个位图`SetIcon`使用每个按钮只能有一个图标。 按下按钮时，该图标将显示向下和向右移动。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&8;](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>CButton::SetImageList  
 调用此方法可设置的图像列表`CButton`对象。  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>参数  
 `pbuttonImagelist`  
 指向新图像列表的指针。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_SETIMAGELIST**消息，如中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)部分[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setnote"></a>CButton::SetNote  
 设置当前 command link 控件的注释文本。  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `lpszNote`|设置为 command link 控件的注释文本的 Unicode 字符串指针。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_COMMANDLINK`或`BS_DEFCOMMANDLINK`。  
  
 此方法可发送[BCM_SETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775977)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_cmdLink`，也就是说，用来以编程方式访问 command link 控件。 在下面的示例使用该变量。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置 command link 控件的注释文本。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&7;](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>CButton::SetSplitGlyph  
 将指定的标志符号与当前的拆分按钮控件相关联。  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `chGlyph`|一个指定要用作拆分按钮的下拉箭头的标志符号的字符。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于具有按钮样式的控件`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 一个标志符号是特定字体中字符的物理表示。 `chGlyph`参数不用作符号，但改为用来从一组系统定义标志符号的选择标志符号。 默认值的下拉箭头标志符号指定的字符"6"，类似于黑色下指三角形 (U +&25;BC) 的 Unicode 字符。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_GLYPH`标志和`himlGlyph`具有成员`chGlyph`参数，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setsplitimagelist"></a>CButton::SetSplitImageList  
 将相关联[图像列表](../../mfc/reference/cimagelist-class.md)与当前的拆分按钮控件。  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pSplitImageList`|指向[CImageList](../../mfc/reference/cimagelist-class.md)要分配给当前的拆分按钮控件。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_IMAGE`标志和`himlGlyph`具有成员`pSplitImageList`参数，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setsplitinfo"></a>CButton::SetSplitInfo  
 指定参数，以确定 Windows 如何绘制当前拆分按钮控件。  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pInfo`|指向[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构，它定义当前拆分按钮控件。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法可发送[BCM_SETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775981)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，也就是说，用来以编程方式访问拆分按钮控件。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例更改用于拆分按钮的下拉箭头的标志符号。 该示例将替换为标志的默认值下指三角形标志符号上指三角形符号。 显示的标志符号取决于你在中指定的字符`himlGlyph`的成员`BUTTON_SPLITINFO`结构。 下指三角形标志符号指定的字符"6 和上指三角形标志符号指定的字符"5。 为了进行比较，请参阅便捷方法， [CButton::SetSplitGlyph](#setsplitglyph)。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&4;](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>CButton::SetSplitSize  
 设置当前的拆分按钮控件的下拉部分的边框。  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pSize`|指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构描述的绑定矩形。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 当扩展拆分按钮控件时，它可以显示下拉菜单的组件，如页导航控件或列表控件。 此方法指定包含下拉列表组件的边框的大小。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_SIZE`标志和`size`具有成员`pSize`参数，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，也就是说，用来以编程方式访问拆分按钮控件。 在下面的示例使用该变量。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例两倍，拆分按钮的下拉箭头的大小。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&5;](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>CButton::SetSplitStyle  
 设置当前的拆分按钮控件的样式。  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `uSplitStyle`|拆分按钮样式按位组合。 有关详细信息，请参阅`uSplitStyle`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 拆分按钮样式指定的对齐方式、 纵横比和图形格式与 Windows 绘制拆分按钮图标。 有关详细信息，请参阅`uSplitStyle`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构与`BCSIF_STYLE`标志和`uSplitStyle`具有成员`uSplitStyle`参数，然后将该结构中发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)中所述的消息[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，也就是说，用来以编程方式访问拆分按钮控件。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置拆分按钮的下拉箭头的样式。 `BCSS_ALIGNLEFT`样式显示按钮，左侧的箭头和`BCSS_STRETCH`样式比例保持不变的下拉箭头时调整大小按钮。  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;&3;](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>CButton::SetState  
 设置突出显示的按钮控件。  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>参数  
 *bHighlight*  
 指定是否要突出显示按钮。 一个非零值会突出显示按钮;值为 0 中删除任何突出显示。  
  
### <a name="remarks"></a>备注  
 突出显示会影响外部的按钮控件。 它不起复选状态的单选按钮或复选框。  
  
 用户单击并按住鼠标左键时，将自动突出显示的按钮控件。 当用户释放鼠标按钮，删除突出显示。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton #&9;](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>CButton::SetTextMargin  
 调用此方法来设置文本的页边空白处`CButton`对象。  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>参数  
 `pmargin`  
 指向新的文本边距的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_SETTEXTMARGIN**消息，如中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)部分[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 类](../../mfc/reference/cscrollbar-class.md)   
 [CStatic 类](../../mfc/reference/cstatic-class.md)   
 [CBitmapButton 类](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)

