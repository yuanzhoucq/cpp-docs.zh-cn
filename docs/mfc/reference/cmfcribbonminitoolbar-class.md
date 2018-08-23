---
title: CMFCRibbonMiniToolBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 789a8165a12977d11220d299e2c99549121dba64
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540990"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar 类
实现上下文快捷工具栏。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|默认构造函数。|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCRibbonMiniToolBar::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|（重写 `CMFCPopupMenu::IsRibbonMiniToolBar`。）|  
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|设置要在工具栏上显示的命令的列表。|  
|[CMFCRibbonMiniToolBar::Show](#show)|在指定的屏幕坐标上显示浮动工具栏。|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|显示浮动工具栏以及上下文菜单。|  
  
## <a name="remarks"></a>备注  
 通常于用户在文档中选择对象后显示浮动工具栏。 例如，用户在文字处理程序中选择文本块后，应用程序将显示包含文本格式设置命令的浮动工具栏。  
  
 鼠标指针位于浮动工具栏边界之外时，浮动工具栏将变透明。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxRibbonMiniToolBar.h  
  
##  <a name="setcommands"></a>  CMFCRibbonMiniToolBar::SetCommands  
 设置要在工具栏上显示的命令的列表。  
  
```  
void SetCommands(
    CMFCRibbonBar* pRibbonBar,  
    const CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>参数  
 [in]*pRibbonBar*  
 浮动工具栏中搜索要显示的按钮在功能区栏。  
  
 [in]*lstCommands*  
 要在浮动工具栏上显示的命令的列表。 所有功能区类别进行搜索以找到关联的按钮。  
  
### <a name="remarks"></a>备注  
 使用此函数设置的命令显示在浮动工具栏的列表。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SetCommands`方法的`CMFCRibbonMiniToolBar`类。 此代码片段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]  
  
##  <a name="show"></a>  CMFCRibbonMiniToolBar::Show  
 在指定的屏幕坐标上显示浮动工具栏。  
  
```  
BOOL Show(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>参数  
 [in]*x*  
 指定屏幕坐标中的浮动工具栏的水平位置。  
  
 [in]*y*  
 指定屏幕坐标中的浮动工具栏的垂直位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则显示浮动工具栏，则返回 TRUE否则为 FALSE。  
  
##  <a name="showwithcontextmenu"></a>  CMFCRibbonMiniToolBar::ShowWithContextMenu  
 显示浮动工具栏以及上下文菜单。  
  
```  
BOOL ShowWithContextMenu(
    int x,  
    int y,  
    UINT uiMenuResID,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>参数  
 [in]*x*  
 屏幕坐标中指定的上下文菜单的水平位置。  
  
 [in]*y*  
 屏幕坐标中指定的上下文菜单的垂直位置。  
  
 [in]*uiMenuResID*  
 指定要显示的上下文菜单的资源 ID。  
  
 [in]*pWndOwner*  
 标识从上下文菜单中接收消息的窗口。  
  
### <a name="return-value"></a>返回值  
 如果已成功，则显示上下文菜单，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此函数用于显示具有上下文菜单的浮动工具栏。 上下文菜单为浮动工具栏下方的定位 15 像素。  
  
##  <a name="iscontextmenumode"></a>  CMFCRibbonMiniToolBar::IsContextMenuMode  
 有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。  
  
```  
BOOL IsContextMenuMode() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isribbonminitoolbar"></a>  CMFCRibbonMiniToolBar::IsRibbonMiniToolBar  
 有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。  
  
```  
virtual BOOL IsRibbonMiniToolBar() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
