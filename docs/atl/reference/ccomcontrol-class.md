---
title: "CComControl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs:
- C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 387d38f89e8d783c7ae85c2ab960d5e59c1c4009
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcontrol-class"></a>CComControl 类
此类提供用于创建和管理 ATL 控件的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class WinBase = CWindowImpl<T>>  
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 实现控件的类。  
  
 *WinBase*  
 实现开窗函数的基本类。 默认为[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComControl::CComControl](#ccomcontrol)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|  
|[CComControl::CreateControlWindow](#createcontrolwindow)|创建该控件的窗口。|  
|[CComControl::FireOnChanged](#fireonchanged)|通知已更改的控件属性的容器的接收器。|  
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|控件属性将要更改以及如何继续执行，该对象要求接收器通知容器的接收器。|  
|[CComControl::MessageBox](#messagebox)|调用此方法来创建、 显示和操作一个消息框。|  
  
## <a name="remarks"></a>备注  
 `CComControl`是一套非常有用的控件帮助器函数和 ATL 控件的基本数据成员。 在创建标准控件或使用 ATL 控件向导 DHTML 控件时，向导将自动派生您的类从`CComControl`。 `CComControl`派生其大多数方法从[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)。  
  
 有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
 有关的演示`CComControl`方法和数据成员，请参阅[CIRC](../../visual-cpp-samples.md)示例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="ccomcontrol"></a>CComControl::CComControl  
 构造函数。  
  
```
CComControl();
```  
  
### <a name="remarks"></a>备注  
 调用[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)构造函数，并传递`m_hWnd`数据成员通过继承[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。  
  
##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface  
 检索指向所请求的接口的指针。  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的 GUID。  
  
 `ppv`  
 [out]指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="remarks"></a>备注  
 仅处理 COM 映射表中的接口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#15;](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow  
 默认情况下，通过调用创建该控件的窗口`CWindowImpl::Create`。  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]父窗口或所有者窗口的句柄。 必须提供有效的窗口句柄。 控制窗口并局限在其父窗口的区域。  
  
 `rcPos`  
 [in]初始大小和要创建窗口的位置。  
  
### <a name="remarks"></a>备注  
 重写此方法，如果您要做些什么而不创建一个窗口，例如，若要创建两个窗口，其中一个将成为您的控件的工具栏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#16;](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>CComControl::FireOnChanged  
 通知已更改的控件属性的容器的接收器。  
  
```
HRESULT FireOnChanged(DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *dispID*  
 [in]已更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果您的控件类派生自[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)，此方法调用[CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged)通知所有连接`IPropertyNotifySink`指定的控件属性已更改的接口。 如果您的控件类不是派生自`IPropertyNotifySink`，此方法返回`S_OK`。 
  
 此方法可以安全地调用即使控件不支持连接点。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#17;](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit  
 控件属性将要更改以及如何继续执行，该对象要求接收器通知容器的接收器。  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *dispID*  
 [in]要更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果您的控件类派生自[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)，此方法调用[CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)通知所有连接`IPropertyNotifySink`即将更改指定的控件属性的接口。 如果您的控件类不是派生自`IPropertyNotifySink`，此方法返回`S_OK`。  

  
 此方法可以安全地调用即使控件不支持连接点。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#18;](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>CComControl::MessageBox  
 调用此方法来创建、 显示和操作一个消息框。  
  
```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 要在消息框中显示的文本。  
  
 `lpszCaption`  
 对话框标题。 如果为 NULL （默认值），使用"错误"的标题。  
  
 `nType`  
 指定的内容和对话框中的行为。 请参阅[MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505)中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]文档，以列表的可用的不同的消息框。 默认值提供了一个简单**确定**按钮。  
  
### <a name="return-value"></a>返回值  
 返回一个整数值，指定下列出的菜单项值之一[MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]文档。  
  
### <a name="remarks"></a>备注  
 `MessageBox`在开发过程中又可以方便地向用户显示的错误或警告消息，则非常有用。  
  
## <a name="see-also"></a>另请参阅  
 [CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComControlBase 类](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl 类](../../atl/reference/ccomcompositecontrol-class.md)

