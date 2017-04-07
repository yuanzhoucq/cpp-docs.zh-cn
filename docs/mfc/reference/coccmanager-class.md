---
title: "COccManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- custom controls [MFC], sites
- COccManager class
- CNoTrackObject class
- ActiveX control containers [C++], control site
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
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
ms.openlocfilehash: 14a75c491a7061d921d6c0c250c6224f4e7d2f04
ms.lasthandoff: 02/24/2017

---
# <a name="coccmanager-class"></a>COccManager 类
管理多个自定义控件站点；通过 `COleControlContainer` 和 `COleControlSite` 对象实现。  
  
## <a name="syntax"></a>语法  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|创建**COleContainer**对象。|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|创建 ActiveX 控件，由关联托管`COleContainer`对象。|  
|[COccManager::CreateSite](#createsite)|创建一个 `COleClientSite` 对象。|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|检索默认按钮的代码。|  
|[COccManager::IsDialogMessage](#isdialogmessage)|确定目标的对话消息。|  
|[COccManager::IsLabelControl](#islabelcontrol)|确定指定的控件是否为一个标签控件。|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|确定当前的助记键是否与指定控件的助记键相匹配。|  
|[COccManager::OnEvent](#onevent)|尝试处理指定的事件。|  
|[COccManager::PostCreateDialog](#postcreatedialog)|释放对话框创建期间分配的资源。|  
|[COccManager::PreCreateDialog](#precreatedialog)|处理 ActiveX 控件的对话框模板。|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|切换指定控件的默认状态。|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|通过指定的对话框模板中的公共控件将任何现有的 ActiveX 控件。|  
  
## <a name="remarks"></a>备注  
 基类， **CNoTrackObject**，是一个未记录的基本类 （位于 AFXTLS。H) 中。 专供 MFC 框架中，类派生自**CNoTrackObject**类不受内存泄漏检测。 建议不要直接从派生**CNoTrackObject**。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxocc.h  
  
##  <a name="createcontainer"></a>COccManager::CreateContainer  
 由框架创建的控件容器调用。  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向与此自定义站点容器关联的窗口对象的指针。  
  
### <a name="return-value"></a>返回值  
 指向新创建的容器;否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 有关创建自定义网站的详细信息，请参阅[COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。  
  
##  <a name="createdlgcontrols"></a>COccManager::CreateDlgControls  
 调用此函数可创建所指定的 ActiveX 控件`pOccDialogInfo`参数。  
  
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
 指向对话框对象的父对象的指针。  
  
 `lpszResourceName`  
 正在创建的资源的名称。  
  
 `pOccDialogInfo`  
 指向用来创建对话框对象的对话框模板的指针。  
  
 `lpResource`  
 指向资源的指针。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则创建控件否则为零。  
  
##  <a name="createsite"></a>COccManager::CreateSite  
 由框架调用以创建控制站点，由指向该容器承载`pCtrlCont`。  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>参数  
 `pCtrlCont`  
 指向承载新控件所在位置的控件容器的指针。  
  
### <a name="return-value"></a>返回值  
 指向新创建的控件所在位置的指针。  
  
### <a name="remarks"></a>备注  
 重写此函数可创建自定义控件站点时，使用您[COleControlSite](../../mfc/reference/colecontrolsite-class.md)的派生类。  
  
 每个控件容器可以承载多个站点。 创建更多的站点具有多个调用`CreateSite`。  
  
##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode  
 调用此函数可确定控件是否为默认按钮。  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 包含按钮控件的窗口对象。  
  
### <a name="return-value"></a>返回值  
 以下值之一：  
  
- **DLGC_DEFPUSHBUTTON**控件是在对话框中的默认按钮。  
  
- **DLGC_UNDEFPUSHBUTTON**控件不是对话框中的默认按钮。  
  
- **0**控件不是一个按钮。  
  
##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage  
 由框架来确定消息是否适用于指定对话框中，如果是，处理的消息调用。  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 *pWndDlg*  
 目标对话框中的消息指向的指针。  
  
 `lpMsg`  
 一个指向`MSG`结构，其中包含要检查的消息。  
  
### <a name="return-value"></a>返回值  
 如果处理了消息; 非零值否则为零。  
  
### <a name="remarks"></a>备注  
 默认行为`IsDialogMessage`是检查键盘消息，并将它们转换为相应的对话框中的选择。 例如，TAB 键，按下时，选择下一个控件或组控件。  
  
 重写此函数可为消息发送到指定的对话框中提供自定义行为。  
  
##  <a name="islabelcontrol"></a>COccManager::IsLabelControl  
 调用此函数可确定指定的控件是一个标签控件。  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向包含该控件的窗口的指针。  
  
### <a name="return-value"></a>返回值  
 非零，如果该控件的标签中;否则为零  
  
### <a name="remarks"></a>备注  
 Label 控件是指像任何控件是下一步在排序中的标签。  
  
##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic  
 调用此函数来确定是否当前的助记键匹配由该控件表示。  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向包含该控件的窗口的指针。  
  
 `lpMsg`  
 一个指向要匹配的消息包含助记键。  
  
### <a name="return-value"></a>返回值  
 如果与助记键匹配的控件，则非零值否则为零  
  
### <a name="remarks"></a>备注  
  
##  <a name="onevent"></a>COccManager::OnEvent  
 由框架来处理指定的事件调用。  
  
```  
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,  
    UINT idCtrl,  
    AFX_EVENT* pEvent,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 *pCmdTarget*  
 一个指向`CCmdTarget`尝试处理该事件对象  
  
 `idCtrl`  
 控件的资源 ID。  
  
 `pEvent`  
 正在处理的事件。  
  
 `pHandlerInfo`  
 如果不是**NULL**，`OnEvent`填入**pTarget**和**pmf**成员**AFX_CMDHANDLERINFO**结构而不调度该命令。 通常情况下，此参数应为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果事件已得到处理，否则为零，非零值。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义默认事件处理过程。  
  
##  <a name="precreatedialog"></a>COccManager::PreCreateDialog  
 由框架之前要处理 ActiveX 控件的对话框模板创建实际对话框中调用。  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>参数  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO**结构，它包含有关对话框模板和承载对话框中的任何 ActiveX 控件的信息。  
  
 *pOrigTemplate*  
 指向要中创建对话框中使用的对话框模板的指针。  
  
### <a name="return-value"></a>返回值  
 指向用于创建对话框的对话框模板结构的指针。  
  
### <a name="remarks"></a>备注  
 默认行为将调用`SplitDialogTemplate`，确定是否存在任何 ActiveX 控件存在，然后返回结果的对话框模板。  
  
 重写此函数可自定义创建一个承载 ActiveX 控件的对话框中的过程。  
  
##  <a name="postcreatedialog"></a>COccManager::PostCreateDialog  
 由框架来释放内存分配的对话框模板调用。  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>参数  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO**结构，它包含有关对话框模板和承载对话框中的任何 ActiveX 控件的信息。  
  
### <a name="remarks"></a>备注  
 此内存分配通过调用`SplitDialogTemplate`，以及所用的任何托管 ActiveX 控件在对话框中。  
  
 重写此函数可自定义清理使用对话框对象的任何资源的过程。  
  
##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton  
 调用此函数可将控件设置为默认按钮。  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向包含该控件的窗口的指针。  
  
 `bDefault`  
 非零，如果该控件应会成为默认按钮;否则为零。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  该控件必须具有**OLEMISC_ACTSLIKEBUTTON**设置状态位。 有关详细信息**OLEMISC**标志，请参见[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)中的主题[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate  
 由框架拆分从公共对话框控件的 ActiveX 控件调用。  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>参数  
 `pTemplate`  
 指向要检查的对话框模板的指针。  
  
 `ppOleDlgItems`  
 指向 ActiveX 控件的对话框框中项的指针的列表。  
  
### <a name="return-value"></a>返回值  
 指向包含仅非 ActiveX 控件的对话框模板结构的指针。 如果没有 ActiveX 控件都不存在， **NULL**返回。  
  
### <a name="remarks"></a>备注  
 如果找到任何 ActiveX 控件，该模板将分析并创建一个新的模板，其中包含只有非 ActiveX 控件。 在此过程中发现所有 ActiveX 控件都添加到`ppOleDlgItems`。  
  
 如果在模板中，没有任何 ActiveX 控件**NULL**返回*。*  
  
> [!NOTE]
>  内存分配的新模板释放中`PostCreateDialog`函数。  
  
 重写此函数可自定义此过程。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)

