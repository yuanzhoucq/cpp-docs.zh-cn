---
title: "CPaneDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e247d1d824d710cfa9588a01d73e1ca611d77ed
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2018
---
# <a name="cpanedialog-class"></a>CPaneDialog 类
`CPaneDialog`类支持一个无模式的可停靠对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|默认构造函数。|  
|`CPaneDialog::~CPaneDialog`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPaneDialog::Create](#create)|创建可停靠对话框中，并将其附加到`CPaneDialog`对象。|  
|`CPaneDialog::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CPaneDialog::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|处理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)消息。 (重新定义了`CBasePane::HandleInitDialog`。)|  
|`CPaneDialog::OnEraseBkgnd`|处理[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)消息。 (重新定义了[CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)。)|  
|`CPaneDialog::OnLButtonDblClk`|处理[WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606)消息。 (重新定义了[CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)。)|  
|`CPaneDialog::OnLButtonDown`|处理[WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607)消息。 (重新定义了[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)。)|  
|`CPaneDialog::OnUpdateCmdUI`|由框架调用以更新对话框窗口。 (重写[cdockablepane:: Onupdatecmdui](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0)。)|  
|`CPaneDialog::OnWindowPosChanging`|处理[WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653)消息。 (重新定义了[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)。)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|指定一个对话框，是的 OLE 控件容器的模板。|  
  
## <a name="remarks"></a>备注  
 构造`CPaneDialog`两个步骤中的对象。 首先，构造你的代码中的对象。 其次，调用[CPaneDialog::Create](#create)。 必须指定有效的资源模板名称或模板 ID，并将指针传递到父窗口。 否则，在创建过程将失败。 对话框中必须指定 WS_CHILD 和 WS_VISIBLE 样式。 我们建议你还指定 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 样式。 有关详细信息，请参阅[窗口样式](styles-used-by-mfc.md#window-styles)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxpanedialog.h  
  
##  <a name="create"></a>  CPaneDialog::Create  
 创建停靠的对话框中，并将其附加到`CPaneDialog`对象。  
  
```  
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID,  
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

 
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszWindowName`  
 停靠的对话框中的名称。  
  
 [in] `pParentWnd`  
 向父窗口的点。  
  
 [in] `bHasGripper`  
 `TRUE` 若要创建带有标题 （控制手柄）; 停靠对话框否则为`FALSE`。  
  
 [in] `lpszTemplateName`  
 资源对话框模板的名称。  
  
 [in] `nStyle`  
 Windows 样式中。  
  
 [in] `nID`  
 控件 id。  
  
 [in] `nIDTemplate`  
 对话框模板资源 ID。  
  
 [in] `dwTabbedStyle`  
 当用户将另一个控制窗格中拖动到此控件窗格的标题会产生的选项卡式窗口的样式。 默认值为 `AFX_CBRS_REGULAR_TABS`。 有关详细信息，请参阅备注部分的[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。  
  
 [in] `dwControlBarStyle`  
 其他样式特性。 默认值为 `AFX_DEFAULT_DOCKING_PANE_STYLE`。 有关详细信息，请参阅备注部分的[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`中的方法`CPaneDialog`类。 此示例摘自[设置窗格大小示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog  
 处理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)消息。  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 [in] `wParam`  
 要接收默认键盘焦点的控件的句柄。  
  
 [in] `lParam`  
 指定附加的初始化数据。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。 此外，`TRUE`将键盘焦点设置为指定的控件`wParam`参数;`FALSE`阻止设置默认键盘焦点。  
  
### <a name="remarks"></a>备注  
 框架使用此方法来初始化控件和一个对话框的外观。 然后再显示对话框中，框架会调用此方法。  
  
##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo  
 指定一个对话框，是的 OLE 控件容器的模板。  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOccDialogInfo`  
 到对话框模板用于创建对话框对象的指针。 此参数的值随后传递到[COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法支持[COccManager](../../mfc/reference/coccmanager-class.md)类，该类管理 OLE 控件站点和 ActiveX 控件。 _AFX_OCC_DIALOG_INFO 结构 afxocc.h 标头文件中定义。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)



