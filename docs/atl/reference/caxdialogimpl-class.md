---
title: CAxDialogImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3e1b7d4f88428060f4aa4d01180bce1e970b650
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365072"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl 类
此类实现一个对话框 （模式或无模式） 承载 ActiveX 控件。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`CAxDialogImpl`。  
  
 *TBase*  
 基窗口类**CDialogImplBaseT**。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|调用此方法以建议或不建议在对象的接收器映射事件映射的所有条目。|  
|[CAxDialogImpl::Create](#create)|调用此方法以创建无模式对话框。|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|调用此方法以销毁无模式对话框。|  
|[CAxDialogImpl::DoModal](#domodal)|调用此方法以创建模式对话框。|  
|[CAxDialogImpl::EndDialog](#enddialog)|调用此方法以销毁模式对话框。|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|调用此方法以获取指向`DialogProc`回调函数。|  
|[CAxDialogImpl::GetIDD](#getidd)|调用此方法以获取对话框模板资源 ID|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|调用此方法以确定消息是否适用于此对话框中，并且如果是，处理消息。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|仅在调试中存在的变量生成并被设置为 true 时为模式对话框。|  
  
## <a name="remarks"></a>备注  
 `CAxDialogImpl` 允许你创建一个模式或无模式对话框。 `CAxDialogImpl` 提供对话框过程，使用默认消息映射来将消息定向到相应的处理程序。  
  
 `CAxDialogImpl` 派生自`CDialogImplBaseT`，它又派生自*TBase* (默认情况下， `CWindow`) 和`CMessageMap`。  
  
 你的类必须定义 IDD 成员，用于指定对话框模板资源 id。 例如，添加 ATL 对话框对象使用**添加类**对话框中会自动将以下行添加到类：  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 其中`MyDialog`是**短名称**在 ATL 对话框向导中输入。  
  
 请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)有关详细信息。  
  
 请注意，使用创建模式对话框上的 ActiveX 控件`CAxDialogImpl`将不支持快捷键。 上一个对话框，使用创建支持快捷键`CAxDialogImpl`，创建一个无模式对话框，并使用你自己的消息循环，使用[CAxDialogImpl::IsDialogMessage](#isdialogmessage)后收到一条消息从队列来处理加速键。  
  
 有关详细信息`CAxDialogImpl`，请参阅[ATL 控件包含常见问题](../../atl/atl-control-containment-faq.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
  
##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap  
 调用此方法以建议或不建议在对象的接收器映射事件映射的所有条目。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>参数  
 `bAdvise`  
 如果所有接收器条目都都可以收到通知;，设置为 true如果所有 false 接收器条目即将成为 unadvised。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="create"></a>  CAxDialogImpl::Create  
 调用此方法以创建无模式对话框。  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]向所有者窗口句柄。  
  
 `dwInitParam`  
 [in]指定要传递给的对话框中的值`lParam`参数**WM_INITDIALOG**消息。  
  
 **RECT （&AMP; A)**  
 未使用此参数。 此参数通过传递在`CComControl`。  
  
### <a name="return-value"></a>返回值  
 新创建的对话框句柄。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CAxDialogImpl`对象。 若要创建模式对话框，请调用[DoModal](#domodal)。  
  
 第二个重写提供为了仅使对话框可以用于[CComControl](../../atl/reference/ccomcontrol-class.md)。  
  
##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow  
 调用此方法以销毁无模式对话框。  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>返回值  
 如果成功销毁窗口; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 不要调用`DestroyWindow`销毁模式对话框。 调用[EndDialog](#enddialog)相反。  
  
##  <a name="domodal"></a>  CAxDialogImpl::DoModal  
 调用此方法以创建模式对话框。  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]向所有者窗口句柄。 默认值是返回值的[正在](http://msdn.microsoft.com/library/windows/desktop/ms646292)Win32 函数。  
  
 `dwInitParam`  
 [in]指定要传递给的对话框中的值`lParam`参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，值`nRetCode`调用中指定的参数[EndDialog](#enddialog); 否则为-1。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CAxDialogImpl`对象。  
  
 若要创建无模式对话框，请调用[创建](#create)。  
  
##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog  
 调用此方法以销毁模式对话框。  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>参数  
 `nRetCode`  
 [in]要返回的值[DoModal](#domodal)。  
  
### <a name="return-value"></a>返回值  
 销毁对话框中; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 `EndDialog` 必须通过对话框过程调用。 对话框时销毁后，Windows 使用的值`nRetCode`的返回值作为`DoModal`，其创建对话框。  
  
> [!NOTE]
>  不要调用`EndDialog`销毁无模式对话框。 调用[DestroyWindow](#destroywindow)相反。  
  
##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc  
 调用此方法以获取指向`DialogProc`回调函数。  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向`DialogProc`回调函数。  
  
### <a name="remarks"></a>备注  
 `DialogProc`函数是一个应用程序定义的回调函数。  
  
##  <a name="getidd"></a>  CAxDialogImpl::GetIDD  
 调用此方法以获取对话框模板资源 id。  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>返回值  
 返回对话框模板资源 id。  
  
##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage  
 调用此方法以确定消息是否适用于此对话框中，并且如果是，处理消息。  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 指向[消息](http://msdn.microsoft.com/library/windows/desktop/ms644958)结构，它包含要检查的消息。  
  
### <a name="return-value"></a>返回值  
 如果消息已处理，则返回 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 此方法旨在要从在消息循环中调用。  
  
##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal  
 仅在调试中存在的变量生成并被设置为 true 时为模式对话框。  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>请参阅  
 [CDialogImpl 类](../../atl/reference/cdialogimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)
