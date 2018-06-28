---
title: COccManager 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
dev_langs:
- C++
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b19b52135678ebd798f61143b5bad953b8629a5
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038144"
---
# <a name="coccmanager-class"></a>COccManager 类
管理多个自定义控件站点；通过 `COleControlContainer` 和 `COleControlSite` 对象实现。  
  
## <a name="syntax"></a>语法  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|创建一个 `COleContainer` 对象。|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|创建 ActiveX 控件，由关联承载`COleContainer`对象。|  
|[COccManager::CreateSite](#createsite)|创建一个 `COleClientSite` 对象。|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|检索默认按钮的代码。|  
|[COccManager::IsDialogMessage](#isdialogmessage)|确定对话框消息的目标。|  
|[COccManager::IsLabelControl](#islabelcontrol)|确定指定的控件是否的标签控件。|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|确定当前的助记键是否与指定控件的助记键相匹配。|  
|[COccManager::OnEvent](#onevent)|尝试处理指定的事件。|  
|[COccManager::PostCreateDialog](#postcreatedialog)|释放在对话框创建过程中分配的资源。|  
|[COccManager::PreCreateDialog](#precreatedialog)|处理 ActiveX 控件的对话框模板。|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|切换指定控件的默认状态。|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|将任何现有的 ActiveX 控件与指定的对话框模板中的公共控件分隔开。|  
  
## <a name="remarks"></a>备注  
 基本类、 `CNoTrackObject`，是一个未记录的基类，（位于 AFXTLS。H) 中。 由 MFC 框架，专供，类派生自`CNoTrackObject`类不受内存泄漏检测。 不建议你直接从派生`CNoTrackObject`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>要求  
 **标头：** afxocc.h  
  
##  <a name="createcontainer"></a>  COccManager::CreateContainer  
 由框架调用以创建的控件容器。  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向与此自定义站点容器关联的窗口对象的指针。  
  
### <a name="return-value"></a>返回值  
 指向新创建的容器;否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 有关创建自定义网站的详细信息，请参阅[COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。  
  
##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls  
 调用此函数可创建指定的 ActiveX 控件*pOccDialogInfo*参数。  
  
```  
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,  
    LPCTSTR lpszResourceName,  
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

 
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,  
    void* lpResource,  
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>参数  
 *pWndParent*  
 指向对话框对象的父级的指针。  
  
 *lpszResourceName*  
 正在创建的资源的名称。  
  
 *pOccDialogInfo*  
 指向用于创建对话框对象的对话框模板的指针。  
  
 *lpResource*  
 指向资源的指针。  
  
### <a name="return-value"></a>返回值  
 如果该控件创建成功; 则为非 0否则为零。  
  
##  <a name="createsite"></a>  COccManager::CreateSite  
 由框架创建控件站点时，由指向该容器承载调用*pCtrlCont*。  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>参数  
 *pCtrlCont*  
 指向托管新的控件所在的控件容器的指针。  
  
### <a name="return-value"></a>返回值  
 指向新创建的控件所在位置的指针。  
  
### <a name="remarks"></a>备注  
 重写此函数可创建自定义控件站点，使用你[COleControlSite](../../mfc/reference/colecontrolsite-class.md)-派生类。  
  
 每个控件容器可以承载多个站点。 创建具有多个调用的其他站点`CreateSite`。  
  
##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode  
 调用此函数可确定控件是否默认下压按钮。  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 包含按钮控件的窗口对象。  
  
### <a name="return-value"></a>返回值  
 以下值之一：  
  
- **DLGC_DEFPUSHBUTTON**控件是在对话框中的默认按钮。  
  
- **DLGC_UNDEFPUSHBUTTON**控件不是对话框中的默认按钮。  
  
- **0**控件不是一个按钮。  
  
##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage  
 由框架调用以确定消息是否适用于指定的对话框中，如果是，处理消息。  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 *pWndDlg*  
 消息的预期的目标对话框指向的指针。  
  
 *lpMsg*  
 指向的指针`MSG`结构，它包含要检查的消息。  
  
### <a name="return-value"></a>返回值  
 如果在处理消息; 非零否则为零。  
  
### <a name="remarks"></a>备注  
 默认行为`IsDialogMessage`是检查键盘消息并将它们转换为相应的对话框中选择。 例如，TAB 键，按下时，选择下一个控件或组控件。  
  
 重写此函数为消息发送到指定的对话框中提供自定义行为。  
  
##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl  
 调用此函数可确定指定的控件是否的标签控件。  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向包含该控件的窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果控件标签; 则为非 0否则为零  
  
### <a name="remarks"></a>备注  
 一个像任何控件是在排序中的下一步的标签的标签控件。  
  
##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic  
 调用此函数来确定是否当前的助记键匹配由该控件。  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向包含该控件的窗口的指针。  
  
 *lpMsg*  
 指向包含助记键的消息，以匹配的指针。  
  
### <a name="return-value"></a>返回值  
 如果助记键匹配的控制，则不为否则为零  
  
### <a name="remarks"></a>备注  
  
##  <a name="onevent"></a>  COccManager::OnEvent  
 由框架调用以处理指定的事件。  
  
```  
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,  
    UINT idCtrl,  
    AFX_EVENT* pEvent,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 *pCmdTarget*  
 指向的指针`CCmdTarget`尝试处理该事件的对象  
  
 *idCtrl*  
 控件的资源 ID。  
  
 *pEvent*  
 正在处理的事件。  
  
 *pHandlerInfo*  
 如果不是**NULL**，`OnEvent`填入**pTarget**和**pmf**的成员**AFX_CMDHANDLERINFO**而不是结构调度该命令。 通常情况下，此参数应**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果事件进行处理，否则为零，则为非 0。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义默认事件处理过程。  
  
##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog  
 由框架调用以在创建实际的对话框之前处理 ActiveX 控件的对话框模板。  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>参数  
 *pOccDialogInfo*  
 **_AFX_OCC_DIALOG_INFO**结构，它包含在对话框模板由对话框承载任何 ActiveX 控件的信息。  
  
 *pOrigTemplate*  
 指向要能在创建对话框中的对话框模板的指针。  
  
### <a name="return-value"></a>返回值  
 指向用于创建对话框中的对话框模板结构的指针。  
  
### <a name="remarks"></a>备注  
 默认行为将调用`SplitDialogTemplate`，确定是否存在任何 ActiveX 控件存在，然后返回结果的对话框模板。  
  
 重写此函数可自定义创建对话框中承载 ActiveX 控件的过程。  
  
##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog  
 由框架调用以释放为对话框模板分配的内存。  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>参数  
 *pOccDialogInfo*  
 **_AFX_OCC_DIALOG_INFO**结构，它包含在对话框模板由对话框承载任何 ActiveX 控件的信息。  
  
### <a name="remarks"></a>备注  
 通过调用分配此内存时`SplitDialogTemplate`，和用于在对话框中的任何托管 ActiveX 控件。  
  
 重写此函数可自定义清理使用对话框对象的任何资源的过程。  
  
##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton  
 调用此函数可将控件设置为默认按钮。  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向包含该控件的窗口的指针。  
  
 *bDefault*  
 如果该控件应会成为默认按钮; 则为非 0否则为零。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  控件必须具有**OLEMISC_ACTSLIKEBUTTON**设置位的状态。 有关详细信息**OLEMISC**标记，请参阅[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) Windows SDK 中的主题。  
  
##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate  
 由框架调用以拆分从公共对话框控件的 ActiveX 控件。  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>参数  
 *pTemplate*  
 指向要检查的对话框模板的指针。  
  
 *ppOleDlgItems*  
 ActiveX 控件的对话框框中项的指针的列表。  
  
### <a name="return-value"></a>返回值  
 指向一个包含仅非 ActiveX 控件的对话框模板结构的指针。 任何 ActiveX 控件是否存在， **NULL**返回。  
  
### <a name="remarks"></a>备注  
 如果找到任何 ActiveX 控件，该模板进行分析，并且创建了包含仅非 ActiveX 控件，一个新模板。 在此过程中发现任何 ActiveX 控件添加到*ppOleDlgItems*。  
  
 如果在模板中，没有任何 ActiveX 控件**NULL**返回 *。*  
  
> [!NOTE]
>  为新模板释放中分配的内存`PostCreateDialog`函数。  
  
 重写此函数可自定义此过程。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)
