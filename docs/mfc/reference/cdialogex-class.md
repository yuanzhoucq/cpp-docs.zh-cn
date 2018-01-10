---
title: "CDialogEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
dev_langs: C++
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c22e258c8306eab1f55fa94f875dde5b68256c71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdialogex-class"></a>CDialogEx 类
`CDialogEx`类指定对话框的背景色和背景图像。  
  
## <a name="syntax"></a>语法  
  
```  
class CDialogEx : public CDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
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
  
 对话框图像存储在资源文件中。 该框架将自动删除从资源文件加载的任何图像。 若要以编程方式删除当前的背景图像，调用[CDialogEx::SetBackgroundImage](#setbackgroundimage)方法或实现`OnDestroy`事件处理程序。 当调用[CDialogEx::SetBackgroundImage](#setbackgroundimage)方法，请传入`HBITMAP`参数作为图像句柄。 如果`CDialogEx`标记是`m_bAutoDestroyBmp`，`TRUE`对象将取得图像的所有权并将其删除。  
  
 A`CDialogEx`对象可以是父级的[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象。 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象调用`CDialogEx::SetActiveMenu`方法时[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象打开。 此后，`CDialogEx`对象处理任何菜单事件，直到[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象已关闭。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdialogex.h  
  
##  <a name="cdialogex"></a>CDialogEx::CDialogEx  
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
  
##  <a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor  
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
  
##  <a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage  
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
 背景图像资源 ID。  
  
 [in] `location`  
 之一`CDialogEx::BackgroundLocation`指定的映像的位置的值。 有效值包括 BACKGR_TILE、 BACKGR_TOPLEFT、 BACKGR_TOPRIGHT、 BACKGR_BOTTOMLEFT 和 BACKGR_BOTTOMRIGHT。 默认值为 BACKGR_TILE。  
  
 [in] `bAutoDestroy`  
 `TRUE`若要自动销毁的背景图像;否则为`FALSE`。  
  
 [in] `bRepaint`  
 `TRUE`若要立即重绘对话框;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 在第二种方法重载语法，`TRUE`方法是否成功; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 你指定的映像不拉伸以适合对话框的工作区。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)
