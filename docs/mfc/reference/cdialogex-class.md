---
title: "CDialogEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogEx
dev_langs:
- C++
helpviewer_keywords:
- CDialogEx class
- CDialogEx::PreTranslateMessage method
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: 27
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
ms.openlocfilehash: c12aa0152fdbf83e423b944a0100045962ddb704
ms.lasthandoff: 02/24/2017

---
# <a name="cdialogex-class"></a>CDialogEx 类
`CDialogEx`类指定对话框的背景色和背景图像。  
  
## <a name="syntax"></a>语法  
  
```  
class CDialogEx : public CDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDialogEx::CDialogEx](#cdialogex)|构造 `CDialogEx` 对象。|  
|`CDialogEx::~CDialogEx`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|设置对话框的背景色。|  
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|设置对话框的背景图像。|  
  
## <a name="remarks"></a>备注  
 若要使用`CDialogEx`类，则从`CDialogEx`类而不是`CDialog`类派生对话框类。  
  
 对话框图像存储在资源文件中。 该框架将自动删除从资源文件加载的任何图像。 若要以编程方式删除当前的背景图像，请调用[CDialogEx::SetBackgroundImage](#setbackgroundimage)方法或实现`OnDestroy`事件处理程序。 当您调用[CDialogEx::SetBackgroundImage](#setbackgroundimage)方法，请传入`HBITMAP`参数作为图像图柄。 如果`CDialogEx`标记是`m_bAutoDestroyBmp`，`TRUE`对象将取得图像的所有权并将其删除。  
  
 一个`CDialogEx`对象可以是父级的[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象。 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象调用`CDialogEx::SetActiveMenu`方法时[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象将会打开。 此后，`CDialogEx`对象处理任何菜单事件，直到[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象已关闭。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdialogex.h  
  
##  <a name="a-namecdialogexa--cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx::CDialogEx  
 构造 `CDialogEx` 对象。  
  
```  
CDialogEx(
    UINT nIDTemplate,  
    CWnd* pParent=NULL);

 
CDialogEx(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIDTemplate`  
 对话框模板资源 ID。  
  
 [in] `lpszTemplateName`  
 对话框模板资源名称。  
  
 [in] `pParent`  
 指向父窗口的指针。 默认值为 `NULL`。  
  
 [in] `pParentWnd`  
 指向父窗口的指针。 默认值为 `NULL`。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetbackgroundcolora--cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor  
 设置对话框的背景色。  
  
```  
void SetBackgroundColor(
    COLORREF color,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 RGB 颜色值。  
  
 [in] `bRepaint`  
 `TRUE`若要立即更新屏幕上。否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetbackgroundimagea--cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage  
 设置对话框的背景图像。  
  
```  
void SetBackgroundImage(
    HBITMAP hBitmap,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bAutoDestroy=TRUE,  
    BOOL bRepaint=TRUE);

 
BOOL SetBackgroundImage(
    UINT uiBmpResId,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `hBitmap`  
 背景图像句柄。  
  
 [in] `uiBmpResId`  
 背景图像的资源 ID。  
  
 [in] `location`  
 其中一个`CDialogEx::BackgroundLocation`指定的映像的位置的值。 有效值包括 BACKGR_TILE、 BACKGR_TOPLEFT、 BACKGR_TOPRIGHT、 BACKGR_BOTTOMLEFT 和 BACKGR_BOTTOMRIGHT。 默认值为 BACKGR_TILE。  
  
 [in] `bAutoDestroy`  
 `TRUE`若要自动销毁的背景图像;否则为`FALSE`。  
  
 [in] `bRepaint`  
 `TRUE`若要立即重绘对话框;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 第二个方法重载的语法中，`TRUE`如果方法成功，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 您指定的图像不拉伸以适合对话框的工作区。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)

