---
title: "CAxDialogImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
dev_langs:
- C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: 21
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 71e77ac6b8d2a89e384817020772bb855ce2d573
ms.lasthandoff: 02/24/2017

---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl 类
此类实现一个对话框 （模式或无模式） 承载 ActiveX 控件。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`CAxDialogImpl`。  
  
 *TBase*  
 基本窗口类**CDialogImplBaseT**。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|调用此方法以建议或不建议在对象的接收器映射事件映射的所有条目。|  
|[CAxDialogImpl::Create](#create)|调用此方法以创建无模式对话框。|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|调用此方法要销毁的无模式对话框。|  
|[CAxDialogImpl::DoModal](#domodal)|调用此方法以创建模式对话框。|  
|[CAxDialogImpl::EndDialog](#enddialog)|调用此方法可销毁一个模式对话框。|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|调用此方法以获取一个指向`DialogProc`回调函数。|  
|[CAxDialogImpl::GetIDD](#getidd)|调用此方法以获取对话框模板资源 ID|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|调用此方法以确定消息是否适用于此对话框中，如果是，处理该消息。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|仅在调试中存在的变量生成并被设置为 true，如果对话框中是模式。|  
  
## <a name="remarks"></a>备注  
 `CAxDialogImpl`允许您创建一个模式对话框或无模式对话框。 `CAxDialogImpl`提供了对话框过程，使用默认消息映射将消息定向到相应的处理程序。  
  
 `CAxDialogImpl`派生自`CDialogImplBaseT`，它又派生自*TBase* (默认情况下， `CWindow`) 和`CMessageMap`。  
  
 您的类必须定义 IDD 成员，用于指定对话框模板资源 id。 例如，添加 ATL 对话框对象使用**添加类**对话框中自动将以下行添加到您的类︰  
  
 [!code-cpp[NVC_ATL_Windowing #&41;](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 其中`MyDialog`是**短名称**在 ATL 对话框向导中输入。  
  
 请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)有关详细信息。  
  
 请注意，上一个模式对话框的 ActiveX 控件使用`CAxDialogImpl`将不支持加速键。 若要支持快捷键上创建一个对话框`CAxDialogImpl`、 创建无模式对话框和使用您自己的消息循环，使用[CAxDialogImpl::IsDialogMessage](#isdialogmessage)后收到一条消息从队列来处理一个加速键。  
  
 有关详细信息`CAxDialogImpl`，请参阅[ATL 控件包含常见问题](../../atl/atl-control-containment-faq.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap  
 调用此方法以建议或不建议在对象的接收器映射事件映射的所有条目。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>参数  
 `bAdvise`  
 如果所有接收器条目都都可以收到通知;，设置为 true如果所有参数为 false 的接收器条目具有将 unadvised。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="create"></a>CAxDialogImpl::Create  
 调用此方法以创建无模式对话框。  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]所有者窗口的句柄。  
  
 `dwInitParam`  
 [in]指定要传递给对话框中的值`lParam`参数**WM_INITDIALOG**消息。  
  
 **RECT.**  
 未使用此参数。 此参数由传入的`CComControl`。  
  
### <a name="return-value"></a>返回值  
 指向新建对话框中的句柄。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CAxDialogImpl`对象。 若要创建模式对话框，请调用[DoModal](#domodal)。  
  
 第二个重写提供为了仅使对话框中可与使用[CComControl](../../atl/reference/ccomcontrol-class.md)。  
  
##  <a name="destroywindow"></a>CAxDialogImpl::DestroyWindow  
 调用此方法要销毁的无模式对话框。  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>返回值  
 如果成功销毁窗口; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 不要调用`DestroyWindow`销毁一个模式对话框。 调用[EndDialog](#enddialog)相反。  
  
##  <a name="domodal"></a>CAxDialogImpl::DoModal  
 调用此方法以创建模式对话框。  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]所有者窗口的句柄。 默认值是返回值的[正在](http://msdn.microsoft.com/library/windows/desktop/ms646292)Win32 函数。  
  
 `dwInitParam`  
 [in]指定要传递给对话框中的值`lParam`参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，值`nRetCode`对调用中指定的参数[EndDialog](#enddialog); 否则为-1。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CAxDialogImpl`对象。  
  
 若要创建无模式对话框，请调用[创建](#create)。  
  
##  <a name="enddialog"></a>CAxDialogImpl::EndDialog  
 调用此方法可销毁一个模式对话框。  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>参数  
 `nRetCode`  
 [in]通过返回的值[DoModal](#domodal)。  
  
### <a name="return-value"></a>返回值  
 销毁对话框中; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 `EndDialog`通过对话框过程，必须调用。 对话框中被销毁后，Windows 将使用的值`nRetCode`的返回值作为`DoModal`，其创建对话框。  
  
> [!NOTE]
>  不要调用`EndDialog`销毁无模式对话框。 调用[DestroyWindow](#destroywindow)相反。  
  
##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc  
 调用此方法以获取一个指向`DialogProc`回调函数。  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向`DialogProc`回调函数。  
  
### <a name="remarks"></a>备注  
 `DialogProc`函数是一个应用程序定义的回调函数。  
  
##  <a name="getidd"></a>CAxDialogImpl::GetIDD  
 调用此方法以获取对话框模板资源 id。  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>返回值  
 返回此对话框模板资源 id。  
  
##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage  
 调用此方法以确定消息是否适用于此对话框中，如果是，处理该消息。  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 指向[MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958)结构，其中包含要检查的消息。  
  
### <a name="return-value"></a>返回值  
 如果消息已处理，则返回 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 此方法用于从一个消息循环中调用。  
  
##  <a name="m_bmodal"></a>CAxDialogImpl::m_bModal  
 仅在调试中存在的变量生成并被设置为 true，如果对话框中是模式。  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>另请参阅  
 [CDialogImpl 类](../../atl/reference/cdialogimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

