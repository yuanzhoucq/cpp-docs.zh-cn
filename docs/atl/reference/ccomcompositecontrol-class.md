---
title: CComCompositeControl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 892cccea65b9e1b6f0c1eec21d3973e84a0fba03
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223254"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 类
此类提供用于实现复合控件所需的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要支持复合控件的任何其他接口也一样。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|构造函数。|  
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|调用此方法以建议或不建议由复合控件承载的所有控件。|  
|[CComCompositeControl::CalcExtent](#calcextent)|调用此方法以计算以 HIMETRIC 为单位的对话框资源用来承载复合控件的大小。|  
|[CComCompositeControl::Create](#create)|调用此方法来创建复合控件的控件窗口。|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|调用此方法来创建控件窗口也建议任何承载的控件。|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|调用此方法以设置使用容器的背景色在复合控件的背景色。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|背景画笔。|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|当前具有焦点的窗口句柄。|  
  
## <a name="remarks"></a>备注  
 类派生自类`CComCompositeControl`继承 ActiveX 复合控件的功能。 ActiveX 控件派生自`CComCompositeControl`所承载的标准对话框。 这些类型的控件称为复合控件，因为它们是可托管其他控件 （Windows 的本机控件和 ActiveX 控件）。  
  
 `CComCompositeControl` 标识可用于通过查找将被子类中的枚举的数据成员来创建复合控件的对话框资源。 IDD 此子类的成员设置为将用作控件的窗口的对话框资源的资源 ID。 以下是示例的类派生自的数据成员的`CComCompositeControl`来标识要用于控件的窗口的对话框资源应包含：  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  复合控件始终是有窗口的控件，但可以包含无窗口控件。  
  
 通过实现的控件，`CComCompositeControl`的派生的类具有按 tab 键行为中生成的默认值。 当该控件接收焦点的所选项卡式到包含应用程序中时，连续按 TAB 键将导致通过所有的复合控件包含的控件，然后带复合控件和到下一项中循环切换焦点容器的 tab 键顺序。 托管控件的 tab 键顺序由对话框资源、 确定的顺序中的 tab 键切换会发生。  
  
> [!NOTE]
>  为了使正常使用的快捷键`CComCompositeControl`，需要根据创建该控件加载快捷键对应表，请将传递的句柄和数量的加速器回[IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，和当释放控件，最后销毁表。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="advisesinkmap"></a>  CComCompositeControl::AdviseSinkMap  
 调用此方法以建议或不建议由复合控件承载的所有控件。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>参数  
 *bAdvise*  
 如果所有控件都都可以收到通知; 则为 true否则为 false。  
  
### <a name="return-value"></a>返回值  
 S_OK  
 事件接收器映射已连接或从其事件源已成功断开连接的所有控件。  
  
 E_FAIL  
 并非所有控制事件接收器映射无法连接或从其事件源已成功断开连接。  
  
 E_POINTER  
 此错误通常表示控件的事件接收器映射中的条目有问题或有问题中使用的模板参数`IDispEventImpl`或`IDispEventSimpleImpl`基类。  
  
 CONNECT_E_ADVISELIMIT  
 连接点已达到其限制的连接，并且无法接受任何详细信息。  
  
 CONNECT_E_CANNOTCONNECT  
 接收器不支持此连接点所需的接口。  
  
 CONNECT_E_NOCONNECTION  
 Cookie 值不表示有效的连接。 此错误通常表示控件的事件接收器映射中的条目有问题或有问题中使用的模板参数`IDispEventImpl`或`IDispEventSimpleImpl`基类。  
  
### <a name="remarks"></a>备注  
 此方法的基实现搜索到这些条目在事件接收器映射。 然后，它将建议或取消通知事件接收器映射接收器项所描述的 COM 对象的连接点。 此成员方法也依赖于派生的类继承的一个实例的事实`IDispEventImpl`接收器映射将建议或 unadvised 中每个控件。  
  
##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent  
 调用此方法以计算以 HIMETRIC 为单位的对话框资源用来承载复合控件的大小。  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>参数  
 *size*  
 对引用`SIZE`结构，以通过此方法来填充。  
  
### <a name="return-value"></a>返回值  
 如果控件承载的对话框; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 在返回的大小*大小*参数。  
  
##  <a name="create"></a>  CComCompositeControl::Create  
 调用此方法来创建复合控件的控件窗口。  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 *hWndParent*  
 控件的父窗口的句柄。  
  
 *rcPos*  
 保留。  
  
 *dwInitParam*  
 若要控制创建期间传递给控件的数据。 数据作为传递*dwInitParam*将显示为的 LPARAM 参数[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)消息，它获取创建时将发送到复合控件。  
  
### <a name="return-value"></a>返回值  
 新创建的复合控件的对话框句柄。  
  
### <a name="remarks"></a>备注  
 通常在控件的就地激活期间调用此方法。  
  
##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl  
 构造函数。  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>备注  
 初始化[CComCompositeControl::m_hbrBackground](#m_hbrbackground)并[CComCompositeControl::m_hWndFocus](#m_hwndfocus)数据成员为 NULL。  
  
##  <a name="dtor"></a>  CComCompositeControl:: ~ CComCompositeControl  
 析构函数。  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>备注  
 如果存在，请删除背景对象。  
  
##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow  
 调用此方法来创建控件窗口也建议任何承载的控件。  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>参数  
 *hWndParent*  
 控件的父窗口的句柄。  
  
 *rcPos*  
 客户端中的复合控件的位置矩形相对于协调*hWndParent*。  
  
### <a name="return-value"></a>返回值  
 返回新创建的复合控件的对话框中的句柄。  
  
### <a name="remarks"></a>备注  
 此方法调用[CComCompositeControl::Create](#create)并[CComCompositeControl::AdviseSinkMap](#advisesinkmap)。  
  
##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground  
 背景画笔。  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus  
 当前具有焦点的窗口句柄。  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient  
 调用此方法以设置使用容器的背景色在复合控件的背景色。  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
## <a name="see-also"></a>请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)   
 [类概述](../../atl/atl-class-overview.md)
