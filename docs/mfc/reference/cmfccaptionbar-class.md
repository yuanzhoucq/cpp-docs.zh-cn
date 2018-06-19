---
title: CMFCCaptionBar 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c40f4d836d662bde1f49b9a0639b771d10db667
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375828"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 类
A`CMFCCaptionBar`对象是可以显示三个元素的控件条： 按钮、 文本标签和位图。 它一次只能显示一种类型的一个元素。 你可以将每个元素与控件进行左对齐、右对齐或居中对齐。 你还可将平面或 3D 样式应用于标题栏的顶部和底部边界。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCCaptionBar::Create](#create)|创建标题栏控件并将其附加到`CMFCCaptionBar`对象。|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|指示是否另一个窗格可以动态插入之间的标题栏和其父框架。 (重写[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|  
|[CMFCCaptionBar::EnableButton](#enablebutton)|启用或禁用的标题栏上的按钮。|  
|[CMFCCaptionBar::GetAlignment](#getalignment)|返回指定元素的对齐方式。|  
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|返回的标题栏的边框大小。|  
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|检索标题栏上的按钮的边框。|  
|[CMFCCaptionBar::GetMargin](#getmargin)|返回标题栏元素的边缘和标题栏控件的边缘之间的距离。|  
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|指定的标题栏是否在消息栏模式下。|  
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|从的标题栏中删除位图图像。|  
|[CMFCCaptionBar::RemoveButton](#removebutton)|从的标题栏中删除按钮。|  
|[CMFCCaptionBar::RemoveIcon](#removeicon)|从的标题栏中删除图标。|  
|[CMFCCaptionBar::RemoveText](#removetext)|从的标题栏中删除的文本标签。|  
|[CMFCCaptionBar::SetBitmap](#setbitmap)|设置标题栏的位图图像。|  
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|设置标题栏的边框大小。|  
|[CMFCCaptionBar::SetButton](#setbutton)|设置标题栏的按钮。|  
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|指定是否按钮始终保持按下。|  
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|设置按钮的工具提示。|  
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|设置标题栏的边框样式。|  
|[CMFCCaptionBar::SetIcon](#seticon)|设置标题栏的图标。|  
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|设置工具提示的标题栏的图像。|  
|[CMFCCaptionBar::SetMargin](#setmargin)|设置标题栏元素的边缘和标题栏控件的边缘之间的距离。|  
|[CMFCCaptionBar::SetText](#settext)|设置标题栏的文本标签。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|由框架调用以填充的标题栏的背景。|  
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|由框架调用以绘制的标题栏的边框。|  
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|由框架调用以绘制标题栏按钮。|  
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|由框架调用以绘制标题栏图像。|  
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|由框架调用以绘制的标题栏文本。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|标题栏背景色。|  
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|在标题栏的边框的颜色。|  
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|标题栏文本的颜色。|  
  
## <a name="remarks"></a>备注  
 若要创建标题栏，请按照下列步骤：  
  
1.  构造 `CMFCCaptionBar` 对象。 通常情况下，你将添加到框架窗口类的标题栏。  
  
2.  调用[CMFCCaptionBar::Create](#create)方法创建标题栏控件并将其附加到`CMFCCaptionBar`对象。  
  
3.  调用[CMFCCaptionBar::SetButton](#setbutton)， [CMFCCaptionBar::SetText](#settext)， [CMFCCaptionBar::SetIcon](#seticon)，和[CMFCCaptionBar::SetBitmap](#setbitmap)设置标题栏元素。  
  
 当你设置的按钮元素时，你必须为该按钮来指定命令 ID。 当用户单击此按钮时，标题栏路由`WM_COMMAND`到父框架窗口具有此 ID 的消息。  
  
 标题栏还可以在消息栏模式下，它们模拟 Microsoft Office 2007 应用程序中显示的消息栏。 在消息栏模式下，标题栏会显示位图、 一条消息和按钮 （这通常将打开一个对话框。）你可以分配到位图的工具提示。  
  
 若要启用消息栏模式，调用[CMFCCaptionBar::Create](#create)并将第四个参数 (bIsMessageBarMode) 设置为`TRUE`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCCaptionBar`类。 该示例演示如何创建标题栏控件、 设置的标题栏的三维边框、 设置以像素为单位的标题栏元素的边缘和标题栏控件的边缘之间的距离，、 设置的标题栏按钮设置按钮的工具提示、 设置的标题栏的文本标签，设置标题栏中，位图图像，以及设置图像的工具提示的标题栏中。 此代码片段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxcaptionbar.h  
  
##  <a name="create"></a>  CMFCCaptionBar::Create  
 创建标题栏控件并将其附加到`CMFCCaptionBar`对象。  
  
```  
BOOL Create(
    DWORD dwStyle,  
    CWnd* pParentWnd,  
    UINT uID,  
    int nHeight=-1,  
    BOOL bIsMessageBarMode=FALSE);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 逻辑或组合的标题栏样式。  
  
 `pParentWnd`  
 标题栏控件的父窗口。  
  
 `uID`  
 标题栏控件的 ID。  
  
 `nHeight`  
 以像素为单位的标题栏控件的高度。 如果它为-1，根据图标、 文本和标题栏控件显示的按钮的高度计算高度。  
  
 `bIsMessageBarMode`  
 `TRUE` 如果标题栏中的消息栏模式;`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果成功，则创建该标题栏控件的创建`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 构造`CMFCCaptionBar`两个步骤中的对象。 首先调用构造函数中，，然后调用`Create`方法，它创建 Windows 控件并将其附加到`CMFCCaptionBar`对象。  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore  
 指示是否另一个窗格可以动态插入之间的标题栏和其父框架。  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`FALSE`除非重写。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton  
 启用或禁用的标题栏上的按钮。  
  
```  
void EnableButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要启用此按钮时，`FALSE`禁用按钮。  
  
##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment  
 返回指定元素的对齐方式。  
  
```  
BarElementAlignment GetAlignment(BarElement elem);
```  
  
### <a name="parameters"></a>参数  
 [in] `elem`  
 为其检索对齐一个标题栏元素。  
  
### <a name="return-value"></a>返回值  
 元素，如按钮、 位图、 文本或图标对齐方式。  
  
### <a name="remarks"></a>备注  
 元素的对齐方式可以是以下值之一：  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize  
 返回的标题栏的边框大小。  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的边框的大小。  
  
##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect  
 检索标题栏上的按钮的边框。  
  
```  
CRect GetButtonRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 A`CRect`包含标题栏上的按钮的边框的坐标的对象。  
  
##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin  
 返回标题栏元素的边缘和标题栏控件的边缘之间的距离。  
  
```  
int GetMargin() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的标题栏元素的边缘和标题栏控件的边缘之间的距离。  
  
##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode  
 指定的标题栏是否在消息栏模式下。  
  
```  
BOOL IsMessageBarMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果标题栏中的消息栏模式;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 在消息栏模式中，标题栏会显示工具提示、 消息文本和一个按钮的图像。  
  
##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground  
 标题栏背景色。  
  
```  
COLORREF m_clrBarBackground  
```  
  
##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder  
 在标题栏的边框的颜色。  
  
```  
COLORREF m_clrBarBorder  
```  
  
##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText  
 标题栏文本的颜色。  
  
```  
COLORREF m_clrBarText  
```  
  
##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground  
 由框架调用以填充的标题栏的背景。  
  
```  
virtual void OnDrawBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的标题栏的指针。  
  
 [in] `rect`  
 要填充的边界矩形。  
  
### <a name="remarks"></a>备注  
 `OnDrawBackground`将要填充的标题栏的背景时调用方法。 默认实现使用填充背景[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)颜色。  
  
 重写此方法在`CMFCCaptionBar`派生类自定义的标题栏的外观。  
  
##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder  
 由框架调用以绘制的标题栏的边框。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 设备上下文，用于显示边框。  
  
 [in] `rect`  
 绑定矩形。  
  
### <a name="remarks"></a>备注  
 默认情况下，边框具有平面样式。  
  
 重写此方法在`CMFCCaptionBar`派生类的标题栏的边框外观进行自定义。  
  
##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton  
 由框架调用以绘制标题栏按钮。  
  
```  
virtual void OnDrawButton(
    CDC* pDC,  
    CRect rect,  
    const CString& strButton,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文，用于显示按钮的指针。  
  
 [in] `rect`  
 按钮的边框。  
  
 [in] `strButton`  
 按钮的文本标签。  
  
 [in] `bEnabled`  
 `TRUE` 如果启用该按钮;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 重写此方法在`CMFCCaptionBar`派生类自定义的标题栏按钮的外观。  
  
##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage  
 由框架调用以绘制标题栏图像。  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向用于显示图像的设备上下文的指针。  
  
 [in] `rect`  
 指定图像的边框。  
  
### <a name="remarks"></a>备注  
 重写此方法在`CMFCCaptionBar`派生类以自定义图像外观。  
  
##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText  
 由框架调用以绘制的标题栏文本。  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文，用于显示按钮的指针。  
  
 [in] `rect`  
 文本的边界的矩形。  
  
 [in] `strText`  
 要显示的文本字符串。  
  
### <a name="remarks"></a>备注  
 默认实现使用显示的文本`CDC::DrawText`和[CMFCCaptionBar::m_clrBarText](#m_clrbartext)颜色。  
  
 重写此方法在`CMFCCaptionBar`派生类自定义的标题栏文本的外观。  
  
##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap  
 从的标题栏中删除位图图像。  
  
```  
void RemoveBitmap();
```  
  
##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton  
 从的标题栏中删除按钮。  
  
```  
void RemoveButton();
```  
  
### <a name="remarks"></a>备注  
 自动调整的标题栏元素布局。  
  
##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon  
 从的标题栏中删除图标。  
  
```  
void RemoveIcon();
```  
  
##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText  
 从的标题栏中删除的文本标签。  
  
```  
void RemoveText();
```  
  
##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap  
 设置标题栏的位图图像。  
  
```  
void SetBitmap(
    HBITMAP hBitmap,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

 
void SetBitmap(
    UINT uiBmpResID,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>参数  
 [in] `hBitmap`  
 要设置的位图句柄。  
  
 [in] `clrTransparent`  
 指定位图的透明颜色的 RGB 值。  
  
 [in] `bStretch`  
 如果`TRUE`，如果不适合于边界矩形映像拉伸位图。 否则位图未延伸。  
  
 [in] `bmpAlignment`  
 位图的对齐方式。  
  
### <a name="remarks"></a>备注  
 此方法用于设置在标题栏上的位图。  
  
 以前的位图将自动销毁。 如果标题栏将显示一个图标，因为你调用了[CMFCCaptionBar::SetIcon](#seticon)方法，除非你通过调用删除图标，将不会显示位图[CMFCCaptionBar::RemoveIcon](#removeicon)。  
  
 对齐位图所指定的`bmpAlignment`参数。  此参数可能是以下 `BarElementAlignment` 值之一：  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize  
 设置标题栏的边框大小。  
  
```  
void SetBorderSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `nSize`  
 新的大小，以像素为单位的标题栏边框。  
  
##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton  
 设置标题栏的按钮。  
  
```  
void SetButton(
    LPCTSTR lpszLabel,  
    UINT uiCmdUI,  
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,  
    BOOL bHasDropDownArrow=TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszLabel`  
 按钮的命令标签。  
  
 `uiCmdUI`  
 按钮的命令 id。  
  
 `btnAlignmnet`  
 按钮的对齐方式。  
  
 `bHasDropDownArrow`  
 `TRUE` 如果按钮会显示一个下拉箭头，`FALSE`否则为。  
  
##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed  
 指定是否按钮始终保持按下。  
  
```  
void SetButtonPressed(BOOL bPresed=TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bPresed`  
 `TRUE` 如果按钮将其按下的状态，保存`FALSE`否则为。  
  
##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip  
 设置按钮的工具提示。  
  
```  
void SetButtonToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszToolTip`  
 工具提示的标题。  
  
 [in] `lpszDescription`  
 工具提示说明中。  
  
##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder  
 设置标题栏的边框样式。  
  
```  
void SetFlatBorder(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bFlat`  
 `TRUE` 如果标题栏边框不变。 `FALSE` 如果边框是三维。  
  
##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon  
 设置标题栏的图标。  
  
```  
void SetIcon(
    HICON hIcon,  
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>参数  
 [in] `hIcon`  
 若要设置图标的句柄。  
  
 [in] `iconAlignment`  
 图标的对齐方式。  
  
### <a name="remarks"></a>备注  
 标题栏可以显示图标或位图集。 请参阅[CMFCCaptionBar::SetBitmap](#setbitmap)若要了解如何显示位图。 如果你设置了图标和位图，将始终显示图标。 调用[CMFCCaptionBar::RemoveIcon](#removeicon)若要删除的标题栏的一个图标。  
  
 图标对齐根据`iconAlignment`参数。 它可以是以下之一`BarElementAlignment`值：  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip  
 设置映像的工具提示的标题栏中。  
  
```  
void SetImageToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszToolTip`  
 工具提示的文本。  
  
 [in] `lpszDescription`  
 工具提示说明中。  
  
##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin  
 设置标题栏元素的边缘和标题栏控件的边缘之间的距离。  
  
```  
void SetMargin(int nMargin);
```  
  
### <a name="parameters"></a>参数  
 [in] `nMargin`  
 以像素为单位的标题栏元素的边缘和标题栏控件的边缘之间的距离。  
  
##  <a name="settext"></a>  CMFCCaptionBar::SetText  
 设置标题栏的文本标签。  
  
```  
void SetText(
    const CString& strText,  
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>参数  
 [in] `strText`  
 要设置的文本字符串。  
  
 [in] `textAlignment`  
 文本对齐方式。  
  
### <a name="remarks"></a>备注  
 对齐的文本标签所指定的`textAlignment`参数。 它可以是以下之一`BarElementAlignment`值：  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
