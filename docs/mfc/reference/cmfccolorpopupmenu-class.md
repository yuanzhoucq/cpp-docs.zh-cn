---
title: "CMFCColorPopupMenu 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu class
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 14076d78eaf86ef01e68656685dd2fd102d96311
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 类
表示一个用户用于选择文档或应用程序中的颜色的弹出菜单。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|构造 `CMFCColorPopupMenu` 对象。|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|创建一个可停靠拖曳颜色栏。 (重写[CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)。)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|返回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)嵌入到弹出菜单。 (重写[CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。)|  
|`CMFCColorPopupMenu::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|设置的属性网格控件对象嵌入的`CMFCColorBar`对象。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|名称|描述|  
|`m_bEnabledInCustomizeMode`|一个布尔值，确定是否显示颜色栏。|  
|`m_wndColorBar`|`CMFCColorBar`对象，它提供颜色选择。|  
  
### <a name="remarks"></a>备注  
 此类继承的弹出菜单功能`CMFCPopupMenu`类，并管理`CMFCColorBar`对象，它提供颜色选择。 自定义模式工具栏框架时与`m_bEnabledInCustomizeMode`成员设置为`FALSE`，颜色栏对象不会显示。 有关自定义模式的详细信息，请参阅[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 有关详细信息`CMFCColorBar`，请参阅[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcolorpopupmenu.h  
  
##  <a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu  
 构造 `CMFCColorPopupMenu` 对象。  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `colors`  
 框架显示弹出菜单的颜色的数组。  
  
 [in] `color`  
 默认值选择颜色。  
  
 [in] `lpszAutoColor`  
 文本标签*自动*（默认值） 颜色按钮或`NULL`。  
  
 自动按钮的标准标签是**自动**。  
  
 [in] `lpszOtherColor`  
 文本标签*其他*按钮，用于显示其他颜色选项，或`NULL`。  
  
 其他按钮的标准标签是**更多颜色...**.  
  
 [in] `lpszDocColors`  
 文档颜色按钮文本标签。 文档颜色调色板列出所有文档当前使用的颜色。  
  
 [in] `lstDocColors`  
 文档当前使用的颜色的列表。  
  
 [in] `nColumns`  
 对颜色数组具有的列数。  
  
 [in] `nHorzDockRows`  
 在颜色栏具有水平停靠时的行数。  
  
 [in] `nVertDockColumns`  
 在颜色栏具有垂直停靠时的列数。  
  
 [in] `colorAutomatic`  
 在框架应用时单击自动按钮的默认颜色。  
  
 [in] `uiCommandID`  
 颜色条控制命令 id。  
  
 [in] `bStdColorDlg`  
 一个布尔值，该值指示是否显示标准系统颜色对话框中或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框。  
  
 [in] `pParentBtn`  
 一个指向父按钮。  
  
 [in] `nID`  
 命令 ID。  
  
### <a name="remarks"></a>备注  
 每个重载构造函数集`m_bEnabledInCustomizeMode`成员`FALSE`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCColorPopupMenu`对象。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&34;](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar  
 创建一个可停靠拖曳颜色栏。  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pWndMain`|分离式栏的父级窗口的指针。|  
|[in] `uiID`|分离式栏的命令 ID。|  
|[in] `lpszName`|分离式栏窗口文本。|  
  
### <a name="return-value"></a>返回值  
 指向新的拖曳控件条对象的指针。  
  
### <a name="remarks"></a>备注  
 此方法创建[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象并将其强制转换[CPane 类](../../mfc/reference/cpane-class.md)指针。 可以将此值强制转换回[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)通过中所述的强制转换宏的指针[MFC 类对象的类型强制转换](../../mfc/reference/type-casting-of-mfc-class-objects.md)。  
  
##  <a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar  
 返回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)嵌入到弹出菜单。  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>返回值  
 指向嵌入的`CMFCPopupMenuBar`。  
  
### <a name="remarks"></a>备注  
 嵌入的颜色弹出菜单还拥有[CMFCPopupMenuBar 类](../../mfc/reference/cmfcpopupmenubar-class.md)对象。 如果您的应用程序使用另一个嵌入的类型，重写此方法在派生类中。  
  
##  <a name="setproplist"></a>CMFCColorPopupMenu::SetPropList  
 设置的属性网格控件对象嵌入的`CMFCColorBar`对象。  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndList`  
 为属性网格控件对象的指针。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

