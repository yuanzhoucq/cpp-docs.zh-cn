---
title: "CButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6e92efe5b5a99042426dd2e6a7594f2de46f2ce
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="cbutton-class"></a>CButton 类
提供 Windows 按钮控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CButton : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CButton::CButton](#cbutton)|构造 `CButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CButton::Create](#create)|创建 Windows 按钮控件并将其附加到`CButton`对象。|  
|[CButton::DrawItem](#drawitem)|若要绘制一个所有者绘制的替代`CButton`对象。|  
|[CButton::GetBitmap](#getbitmap)|检索与以前设置的位图的句柄[SetBitmap](#setbitmap)。|  
|[CButton::GetButtonStyle](#getbuttonstyle)|检索有关按钮控件样式信息。|  
|[CButton::GetCheck](#getcheck)|检索一个按钮控件的复选状态。|  
|[CButton::GetCursor](#getcursor)|检索与以前设置的光标图像句柄[SetCursor](#setcursor)。|  
|[CButton::GetIcon](#geticon)|检索与以前设置的图标的句柄[SetIcon](#seticon)。|  
|[CButton::GetIdealSize](#getidealsize)|检索按钮控件的理想大小。|  
|[CButton::GetImageList](#getimagelist)|检索该按钮控件的图像列表。|  
|[CButton::GetNote](#getnote)|检索当前命令链接控件的注意组件。|  
|[CButton::GetNoteLength](#getnotelength)|检索当前命令链接控件的注释文本的长度。|  
|[CButton::GetSplitGlyph](#getsplitglyph)|检索与当前的拆分按钮控件关联的标志符号。|  
|[CButton::GetSplitImageList](#getsplitimagelist)|检索当前的拆分按钮控件的图像列表。|  
|[CButton::GetSplitInfo](#getsplitinfo)|检索定义当前拆分按钮控件的信息。|  
|[CButton::GetSplitSize](#getsplitsize)|检索当前的拆分按钮控件的下拉部分的绑定矩形。|  
|[CButton::GetSplitStyle](#getsplitstyle)|检索定义当前拆分按钮控件的拆分按钮样式。|  
|[CButton::GetState](#getstate)|检索的检查状态，突出显示状态和焦点状态的按钮控件。|  
|[CButton::GetTextMargin](#gettextmargin)|检索该按钮控件的文本边距。|  
|[CButton::SetBitmap](#setbitmap)|指定要显示在按钮上的位图。|  
|[CButton::SetButtonStyle](#setbuttonstyle)|更改按钮的样式。|  
|[CButton::SetCheck](#setcheck)|设置按钮控件的复选状态。|  
|[CButton::SetCursor](#setcursor)|指定要在按钮上显示的光标映像。|  
|[CButton::SetDropDownState](#setdropdownstate)|设置当前的拆分按钮控件的下拉列表状态。|  
|[CButton::SetIcon](#seticon)|指定要在按钮上显示的图标。|  
|[CButton::SetImageList](#setimagelist)|设置按钮控件的图像列表。|  
|[CButton::SetNote](#setnote)|设置当前命令链接控件上的备注。|  
|[CButton::SetSplitGlyph](#setsplitglyph)|将指定的标志符号与当前的拆分按钮控件相关联。|  
|[CButton::SetSplitImageList](#setsplitimagelist)|将图像列表与当前的拆分按钮控件相关联。|  
|[CButton::SetSplitInfo](#setsplitinfo)|指定定义当前拆分按钮控件的信息。|  
|[CButton::SetSplitSize](#setsplitsize)|设置当前的拆分按钮控件的下拉部分的边框。|  
|[CButton::SetSplitStyle](#setsplitstyle)|设置当前的拆分按钮控件的样式。|  
|[CButton::SetState](#setstate)|设置按钮控件的突出显示状态。|  
|[CButton::SetTextMargin](#settextmargin)|设置按钮控件的文本边距。|  
  
## <a name="remarks"></a>备注  
 按钮控件是可通过单击打开和关闭一个小的矩形的子窗口。 按钮可单独使用或在组和可以进行标记或不包含文本显示。 当用户单击它时，一个按钮通常会更改外观。  
  
 典型的按钮，复选框、 单选按钮和按钮。 A`CButton`对象都能成为任一这些，根据[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)指定在由其初始化[创建](#create)成员函数。  
  
 此外， [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)类派生自`CButton`支持创建使用位图图像而非文本进行标记的按钮控件。 A`CBitmapButton`可以有单独的位图按钮将上、 下、 已设定焦点，和禁用状态。  
  
 从对话框模板或直接在代码中，可以创建一个按钮控件。 在这两种情况下，第一次调用的构造函数`CButton`构造`CButton`对象; 然后调用**创建**成员函数来创建 Windows 按钮控件，然后将其附加到`CButton`对象。  
  
 构造可以是派生自类中的一步过程`CButton`。 编写派生的类和调用构造函数**创建**从构造函数中。  
  
 如果你想要处理到其父发送的按钮控件的 Windows 通知消息 (通常从派生的类[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。  
  
 每个消息映射条目采用以下形式：  
  
 **ON_**通知**(**`id`， `memberFxn` **)**  
  
 其中`id`指定发送通知的控件的子窗口 ID 和`memberFxn`是父成员函数编写以处理通知的名称。  
  
 父元素的函数原型如下所示：  
  
 **afx_msg** `void` `memberFxn` **（);**  
  
 潜在的消息映射条目如下所示：  
  
|映射条目|发送到父时...|  
|---------------|----------------------------|  
|**ON_BN_CLICKED**|用户单击按钮。|  
|**ON_BN_DOUBLECLICKED**|用户双击一个按钮。|  
  
 如果你创建`CButton`对象通过对话框资源，`CButton`当用户关闭对话框中，将自动销毁对象。  
  
 如果你创建`CButton`对象在窗口中，你可能需要将其销毁。 如果你创建`CButton`使用堆上的对象**新**函数，必须调用**删除**对象销毁它，当用户关闭 Windows 按钮控件。 如果你创建`CButton`堆栈，或它的对象为嵌入在父对话框对象，它自动销毁。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="cbutton"></a>CButton::CButton  
 构造 `CButton` 对象。  
  
```  
CButton();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>CButton::Create  
 创建 Windows 按钮控件并将其附加到`CButton`对象。  
  
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
 指定按钮控件的样式。 应用的任意组合[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)到按钮。  
  
 `rect`  
 指定按钮控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。  
  
 `pParentWnd`  
 指定按钮控件的父窗口中，通常`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定按钮控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CButton`两个步骤中的对象。 首先，调用的构造函数，然后调用**创建**，它创建 Windows 按钮控件并将其附加到`CButton`对象。  
  
 如果**WS_VISIBLE**给定样式，Windows 将按钮控件将发送激活和显示按钮所需的所有消息。  
  
 将应用以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到按钮控件：  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**与组控件  
  
- **WS_TABSTOP**要包括在 tab 键顺序中的按钮  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>CButton::DrawItem  
 当所有者描述的按钮的可视方位发生更改时由框架调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的长指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构。 结构包含有关要绘制的项和绘图所需的类型信息。  
  
### <a name="remarks"></a>备注  
 所有者描述的按钮有**BS_OWNERDRAW**样式集。 重写该成员函数以实现一个所有者绘制的绘图`CButton`对象。 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`在该成员之前函数将终止。  
  
 另请参阅[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)样式的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>CButton::GetBitmap  
 调用此成员函数可获取与以前设置的位图的句柄[SetBitmap](#setbitmap)，即与按钮相关联。  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向位图的句柄。 **NULL**如果以前指定不使用位图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>CButton::GetButtonStyle  
 检索有关按钮控件样式信息。  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回此按钮样式`CButton`对象。 此函数仅返回[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)样式值，不是任何其他窗口样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>CButton::GetCheck  
 检索的单选按钮或复选框的选中状态。  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>返回值  
 按钮控件中的返回值创建与**BS_AUTOCHECKBOX**， **BS_AUTORADIOBUTTON**， **BS_AUTO3STATE**， **BS_CHECKBOX**， **BS_RADIOBUTTON**，或**BS_3STATE**样式是以下值之一：  
  
|“值”|含义|  
|-----------|-------------|  
|**BST_UNCHECKED**|按钮状态为未选中状态。|  
|**BST_CHECKED**|将检查按钮状态。|  
|**BST_INDETERMINATE**|按钮状态是不确定的 (仅适用于该按钮具有**BS_3STATE**或**BS_AUTO3STATE**样式)。|  
  
 如果该按钮具有任何其他样式，则返回值是**BST_UNCHECKED**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>CButton::GetCursor  
 调用此成员函数可获取光标，与以前设置的句柄[SetCursor](#setcursor)，即与按钮相关联。  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>返回值  
 光标图像句柄。 **NULL**如果以前不指定任何光标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>CButton::GetIcon  
 调用此成员函数可获取与以前设置的图标的句柄[SetIcon](#seticon)，即与按钮相关联。  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>返回值  
 图标的图柄。 **NULL**如果以前指定无图标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CButton::GetIdealSize  
 检索该按钮控件的理想大小。  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>参数  
 *psize*  
 指向按钮的当前大小的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_GETIDEALSIZE**消息中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)的 Windows sdk 的部分。  
  
##  <a name="getimagelist"></a>CButton::GetImageList  
 调用此方法以获取从按钮控件的图像列表。  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>参数  
 `pbuttonImagelist`  
 指向的图像列表的指针`CButton`对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_GETIMAGELIST**消息中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)的 Windows sdk 的部分。  
  
##  <a name="getnote"></a>CButton::GetNote  
 检索与当前的命令链接控件关联的注释文本。  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `lpszNote`|指向调用方负责分配和取消分配缓冲区的指针。 如果返回值为`true`、 在缓冲区中包含与当前的命令链接控件相关联; 否则为便笺文本、 缓冲区保持不变。|  
|[in, out] `cchNote`|指向一个无符号的整数变量的指针。<br /><br /> 当调用此方法时，该变量包含指定的缓冲区的大小`lpszNote`参数。<br /><br /> 此方法返回时，如果返回值为`true`变量包含的大小与当前的命令链接控件相关联的注释。 如果返回值为`false`，该变量包含包含注释所需的缓冲区大小。|  
  
### <a name="return-value"></a>返回值  
 在第一个重载中， [CString](../../atl-mfc-shared/using-cstring.md)对象，其中包含与当前的命令链接控件关联的注释文本。  
  
 或  
  
 在第二个重载中，`true`如果此方法成功; 否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_COMMANDLINK`或`BS_DEFCOMMANDLINK`。  
  
 此方法可发送[BCM_GETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775965)消息，Windows SDK 中介绍。  
  
##  <a name="getnotelength"></a>CButton::GetNoteLength  
 检索当前命令链接控件的注释文本的长度。  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 16 位 Unicode 字符，用于当前命令链接控件中的注意文本的长度。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_COMMANDLINK`或`BS_DEFCOMMANDLINK`。  
  
 此方法可发送[BCM_GETNOTELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb775967)消息，Windows SDK 中介绍。  
  
##  <a name="getsplitglyph"></a>CButton::GetSplitGlyph  
 检索与当前的拆分按钮控件关联的标志符号。  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>返回值  
 与当前的拆分按钮控件关联的标志符号字符。  
  
### <a name="remarks"></a>备注  
 标志符号是字符的物理表示形式中特定字体。 例如，可能会使用复选标记的 Unicode 字符的标志符号修饰拆分按钮控件 (U + 2713)。  
  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_GLYPH`标志，然后结构中的发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)描述消息在 Windows SDK 中。 当消息函数返回时，此方法检索从标志符号`himlGlyph`结构中的成员。  
  
##  <a name="getsplitimagelist"></a>CButton::GetSplitImageList  
 检索[图像列表](../../mfc/reference/cimagelist-class.md)当前拆分按钮控件。  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CImageList](../../mfc/reference/cimagelist-class.md)对象。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_IMAGE`标志，然后结构中的发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)描述消息在 Windows SDK 中。 当消息函数返回时，此方法检索从图像列表`himlGlyph`结构中的成员。  
  
##  <a name="getsplitinfo"></a>CButton::GetSplitInfo  
 检索确定 Windows 如何绘制当前拆分按钮控件的参数。  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pInfo`|指向[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)接收当前拆分按钮控件有关的信息的结构。 调用方负责分配结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法可发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)消息，Windows SDK 中介绍。  
  
##  <a name="getsplitsize"></a>CButton::GetSplitSize  
 检索当前的拆分按钮控件的下拉部分的绑定矩形。  
  
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
  
 当扩展拆分按钮控件时，它可以显示如列表控件或页导航控件的下拉列表组件。 此方法检索包含下拉列表组件的绑定矩形。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_SIZE`标志，然后结构中的发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)描述消息在 Windows SDK 中。 当消息函数返回时，此方法检索从边框`size`结构中的成员。  
  
##  <a name="getsplitstyle"></a>CButton::GetSplitStyle  
 检索定义当前拆分按钮控件的拆分按钮样式。  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 拆分按钮样式按位组合。 有关详细信息，请参阅`uSplitStyle`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 拆分按钮样式指定对齐方式、 纵横比和与其 Windows 绘制拆分按钮图标的图形格式。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_STYLE`标志，然后结构中的发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969)描述消息在 Windows SDK 中。 当消息函数返回时，此方法检索中的拆分按钮样式`uSplitStyle`结构中的成员。  
  
##  <a name="getstate"></a>CButton::GetState  
 检索一个按钮控件的状态。  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含指示按钮控件的当前状态的值的组合的位字段。 下表列出可能的值。  
  
|按钮状态|“值”|描述|  
|------------------|-----------|-----------------|  
|`BST_UNCHECKED`|0x0000|初始状态。|  
|`BST_CHECKED`|从 0x0001|已选中按钮控件。|  
|`BST_INDETERMINATE`|0x0002|状态是不确定 （才有可能在按钮控件有三种状态时）。|  
|`BST_PUSHED`|0x0004|按下按钮控件。|  
|`BST_FOCUS`|0x0008|按钮控件具有焦点。|  
  
### <a name="remarks"></a>备注  
 具有的按钮控件`BS_3STATE`或`BS_AUTO3STATE`按钮样式创建一个具有名为不确定状态的第三个状态的复选框。 不确定状态表示复选框已选中和取消选中都不。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>CButton::GetTextMargin  
 调用此方法以获取的文本边距`CButton`对象。  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>参数  
 `pmargin`  
 指向的文本边距`CButton`对象。  
  
### <a name="return-value"></a>返回值  
 返回文本边距。  
  
### <a name="remarks"></a>备注  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_GETTEXTMARGIN**消息中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)的 Windows sdk 的部分。  
  
##  <a name="setbitmap"></a>CButton::SetBitmap  
 调用此成员函数以将新的位图与按钮相关联。  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 位图的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与按钮相关联的位图的句柄。  
  
### <a name="remarks"></a>备注  
 位图将自动放置默认居中的按钮的表面上。 如果位图按钮太大，则将剪辑任意一侧。 你可以选择其他对齐选项，其中包括：  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 与不同[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它使用每个按钮，四个位图`SetBitmap`使用每个按钮的只有一个位图。 按下按钮时，位图显示向下和向右移动。  
  
 你负责使用它完成后释放位图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>CButton::SetButtonStyle  
 更改按钮的样式。  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nStyle`  
 指定[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。  
  
 `bRedraw`  
 指定是否要重新绘制按钮。 一个非零值重绘按钮。 0 值不会刷新按钮。 默认情况下重绘按钮。  
  
### <a name="remarks"></a>备注  
 使用`GetButtonStyle`成员函数来检索按钮样式。 完成按钮样式的低序位字是特定于按钮的样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>CButton::SetCheck  
 设置或重置的单选按钮或复选框的复选状态。  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>参数  
 `nCheck`  
 指定的复选状态。 此参数可以是以下项之一：  
  
|“值”|含义|  
|-----------|-------------|  
|**BST_UNCHECKED**|将按钮状态设置为未选中状态。|  
|**BST_CHECKED**|将按钮状态，检查设置。|  
|**BST_INDETERMINATE**|将按钮状态设置为不确定。 可以使用此值，仅当该按钮具有**BS_3STATE**或**BS_AUTO3STATE**样式。|  
  
### <a name="remarks"></a>备注  
 此成员函数具有对某个按钮没有影响。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>CButton::SetCursor  
 调用此成员函数以将新光标与按钮相关联。  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>参数  
 `hCursor`  
 光标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与按钮相关联光标的句柄。  
  
### <a name="remarks"></a>备注  
 光标将自动放置默认居中的按钮的表面上。 如果光标位于按钮太大，则将剪辑任意一侧。 你可以选择其他对齐选项，其中包括：  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 与不同[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它使用每个按钮，四个位图`SetCursor`使用每个按钮的只有一个游标。 按下按钮时，光标将显示向下和向右移动。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>CButton::SetDropDownState  
 设置当前的拆分按钮控件的下拉列表状态。  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `fDropDown`|`true`若要设置`BST_DROPDOWNPUSHED`状态; 否则为`false`。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 拆分按钮控件具有的样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`它包括一个按钮和一个向右侧的下拉箭头。 有关详细信息，请参阅[按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)。 通常情况下，下拉列表状态将设置当用户单击下拉箭头。 使用此方法以编程方式设置控件的下拉列表状态。 下拉箭头绘制阴影来指示的状态。  
  
 此方法可发送[BCM_SETDROPDOWNSTATE](http://msdn.microsoft.com/library/windows/desktop/bb775973)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，即用于以编程方式访问拆分按钮控件。 在下面的示例使用此变量。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置拆分按钮控件，以指示推送的下拉箭头的状态。  
  
 [!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>CButton::SetElevationRequired  
 设置为当前的按钮控件的状态`elevation required`，这是必需的控件以显示一个提升的安全图标。  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `fElevationRequired`|`true`若要设置`elevation required`状态; 否则为`false`。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果按钮或命令的链接控件需要提升的安全权限来执行操作，将控件设置为`elevation required`状态。 随后，Windows 将显示用户帐户控制 (UAC) 防火墙图标在控件上。 详细信息，请参阅"用户帐户控制"在[MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507)。  
  
 此方法可发送[BCM_SETSHIELD](http://msdn.microsoft.com/library/windows/desktop/bb775979)消息，Windows SDK 中介绍。  
  
##  <a name="seticon"></a>CButton::SetIcon  
 调用此成员函数以将新的图标与按钮相关联。  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 `hIcon`  
 图标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与按钮相关联的图标的句柄。  
  
### <a name="remarks"></a>备注  
 图标将自动放置默认居中的按钮的表面上。 如果图标按钮太大，则将剪辑任意一侧。 你可以选择其他对齐选项，其中包括：  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 与不同[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它使用每个按钮，四个位图`SetIcon`使用每个按钮的只有一个图标。 按下按钮时，该图标将显示向下和向右移动。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>CButton::SetImageList  
 调用此方法以设置的图像列表`CButton`对象。  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>参数  
 `pbuttonImagelist`  
 指向新的图像列表的指针。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功后， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_SETIMAGELIST**消息中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)的 Windows sdk 的部分。  
  
##  <a name="setnote"></a>CButton::SetNote  
 设置当前命令链接控件的注释文本。  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `lpszNote`|为设置为命令链接控件的注释文本的 Unicode 字符串的指针。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_COMMANDLINK`或`BS_DEFCOMMANDLINK`。  
  
 此方法可发送[BCM_SETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775977)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_cmdLink`，即用于以编程方式访问命令链接控件。 在下面的示例使用此变量。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置命令链接控件的注释文本。  
  
 [!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>CButton::SetSplitGlyph  
 将指定的标志符号与当前的拆分按钮控件相关联。  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `chGlyph`|指定要使用作为拆分按钮下拉箭头的标志符号的字符。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 仅对具有按钮样式的控件使用此方法`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 标志符号是字符的物理表示形式中特定字体。 `chGlyph`参数不用作符号，但改为将其用于将从系统定义的标志符号的一组选择标志符号。 默认下拉箭头字形指定"6"的字符，类似于黑色下指三角形 (U + 25BC) 的 Unicode 字符。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_GLYPH`标志和`himlGlyph`成员`chGlyph`参数，然后在结构的将发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) Windows SDK 中介绍的消息。  
  
##  <a name="setsplitimagelist"></a>CButton::SetSplitImageList  
 将相关联[图像列表](../../mfc/reference/cimagelist-class.md)与当前的拆分按钮控件。  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `pSplitImageList`|指向[CImageList](../../mfc/reference/cimagelist-class.md)要分配给当前的拆分按钮控件。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_IMAGE`标志和`himlGlyph`成员`pSplitImageList`参数，然后在结构的将发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) Windows SDK 中介绍的消息。  
  
##  <a name="setsplitinfo"></a>CButton::SetSplitInfo  
 指定确定如何 Windows 绘制当前拆分按钮控件的参数。  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `pInfo`|指向[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构，它定义当前拆分按钮控件。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 此方法可发送[BCM_SETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775981)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，即用于以编程方式访问拆分按钮控件。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将更改用于拆分按钮下拉箭头的标志符号。 该示例替换为标志的默认下指三角形标志符号上指三角形符号。 显示的标志符号取决于你在中指定的字符`himlGlyph`的成员`BUTTON_SPLITINFO`结构。 下指三角形标志符号指定的字符"6 和上指三角形标志符号指定的字符"5。 有关比较，请参阅便捷方法， [CButton::SetSplitGlyph](#setsplitglyph)。  
  
 [!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>CButton::SetSplitSize  
 设置当前的拆分按钮控件的下拉部分的边框。  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `pSize`|指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)描述边界的矩形的结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 当扩展拆分按钮控件时，它可以显示如列表控件或页导航控件的下拉列表组件。 此方法指定包含下拉列表组件的边框的大小。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_SIZE`标志和`size`成员`pSize`参数，然后在结构的将发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) Windows SDK 中介绍的消息。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，即用于以编程方式访问拆分按钮控件。 在下面的示例使用此变量。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将拆分按钮下拉箭头的大小扩大一倍。  
  
 [!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>CButton::SetSplitStyle  
 设置当前的拆分按钮控件的样式。  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `uSplitStyle`|拆分按钮样式按位组合。 有关详细信息，请参阅`uSplitStyle`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法只能用于的控制其按钮样式`BS_SPLITBUTTON`或`BS_DEFSPLITBUTTON`。  
  
 拆分按钮样式指定对齐方式、 纵横比和与其 Windows 绘制拆分按钮图标的图形格式。 有关详细信息，请参阅`uSplitStyle`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构。  
  
 此方法初始化`mask`的成员[BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955)结构`BCSIF_STYLE`标志和`uSplitStyle`成员`uSplitStyle`参数，然后在结构的将发送[BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) Windows SDK 中介绍的消息。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_splitButton`，即用于以编程方式访问拆分按钮控件。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置拆分按钮下拉箭头的样式。 `BCSS_ALIGNLEFT`样式显示此按钮时，左侧的箭头和`BCSS_STRETCH`样式比例保持不变的下拉箭头时调整大小的按钮。  
  
 [!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>CButton::SetState  
 设置是否或不突出显示按钮控件。  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>参数  
 *bHighlight*  
 指定是否会突出显示按钮。 一个非零值突出显示该按钮;0 值中删除任何突出显示。  
  
### <a name="remarks"></a>备注  
 突出显示会影响按钮控件的外部。 它不起上的单选按钮或复选框的选中状态。  
  
 用户单击并按住鼠标左键时，将自动突出显示按钮控件。 当用户释放鼠标按钮，删除突出显示。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>CButton::SetTextMargin  
 调用此方法以设置的文本边距`CButton`对象。  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>参数  
 `pmargin`  
 指向新的文本边距的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能**BCM_SETTEXTMARGIN**消息中所述[按钮](http://msdn.microsoft.com/library/windows/desktop/bb775943)的 Windows sdk 的部分。  
  
## <a name="see-also"></a>请参阅  
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
