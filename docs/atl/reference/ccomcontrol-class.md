---
title: CComControl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6017d06715146a0440887a2a2e10828398d5044b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365543"
---
# <a name="ccomcontrol-class"></a>CComControl 类
此类提供用于创建和管理 ATL 控件的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
  
|名称|描述|  
|----------|-----------------|  
|[CComControl::CComControl](#ccomcontrol)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|  
|[CComControl::CreateControlWindow](#createcontrolwindow)|创建控件的窗口。|  
|[CComControl::FireOnChanged](#fireonchanged)|通知的控件属性已更改的容器的接收器。|  
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|验证的控件属性将要发生更改，以及如何继续执行，该对象要求接收器通知容器的接收器。|  
|[CComControl::MessageBox](#messagebox)|调用此方法以创建、 显示和操作的消息框。|  
  
## <a name="remarks"></a>备注  
 `CComControl` 是一组非常有用的控件帮助器函数和 ATL 控件的重要数据成员。 当你创建的标准控件或使用 ATL 控件向导 DHTML 控件时，该向导将自动派生您的类从`CComControl`。 `CComControl` 派生从其方法中的大多数[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)。  
  
 有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有关 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
 有关演示`CComControl`方法和数据成员，请参阅[CIRC](../../visual-cpp-samples.md)示例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="ccomcontrol"></a>  CComControl::CComControl  
 构造函数。  
  
```
CComControl();
```  
  
### <a name="remarks"></a>备注  
 调用[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)构造函数，并传递`m_hWnd`数据成员通过继承[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。  
  
##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface  
 检索指向所请求的接口的指针。  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求接口的 GUID。  
  
 `ppv`  
 [out]指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="remarks"></a>备注  
 仅处理 COM 映射表中的接口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow  
 默认情况下，通过调用创建控件的窗口`CWindowImpl::Create`。  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]父或所有者窗口的句柄。 必须提供有效的窗口句柄。 控制窗口范围限制为其父窗口的区域。  
  
 `rcPos`  
 [in]初始大小和窗口要创建的位置。  
  
### <a name="remarks"></a>备注  
 重写此方法，如果你想要执行某些操作之外创建一个窗口，例如，若要创建两个窗口，其中将成为工具栏为您的控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>  CComControl::FireOnChanged  
 通知的控件属性已更改的容器的接收器。  
  
```
HRESULT FireOnChanged(DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *dispID*  
 [in]已更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果你的控件类派生自[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)，此方法调用[CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged)通知所有连接`IPropertyNotifySink`接口的指定的控件属性已更改。 如果你的控件类不是派生自`IPropertyNotifySink`，此方法返回`S_OK`。 
  
 此方法调用是安全即使控件不支持连接点。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit  
 验证的控件属性将要发生更改，以及如何继续执行，该对象要求接收器通知容器的接收器。  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *dispID*  
 [in]要更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果你的控件类派生自[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)，此方法调用[CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)通知所有连接`IPropertyNotifySink`接口的指定控件属性即将更改。 如果你的控件类不是派生自`IPropertyNotifySink`，此方法返回`S_OK`。  

  
 此方法调用是安全即使控件不支持连接点。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>  CComControl::MessageBox  
 调用此方法以创建、 显示和操作的消息框。  
  
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
 对话框标题。 如果 NULL （默认值），使用"Error"的标题。  
  
 `nType`  
 指定的内容和对话框中的行为。 请参阅[MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505)可用的不同的消息框的列表的 Windows SDK 文档中的条目。 默认值提供一个简单的**确定**按钮。  
  
### <a name="return-value"></a>返回值  
 返回一个整数值，指定下列出的菜单项值之一[MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) Windows SDK 文档中。  
  
### <a name="remarks"></a>备注  
 `MessageBox` 同时在开发过程和向用户显示错误或警告消息的简单办法，则非常有用。  
  
## <a name="see-also"></a>请参阅  
 [CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComControlBase 类](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl 类](../../atl/reference/ccomcompositecontrol-class.md)
