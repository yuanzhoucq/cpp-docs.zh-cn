---
title: "CComCompositeControl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a7d7b14d67a127fadd8199f9cf9e1e209b8eea7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 类
此类提供实现的复合控件所需的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要为您的复合控件支持很好地从任何其他接口。  
  
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
|[CComCompositeControl::CalcExtent](#calcextent)|调用此方法以计算的大小以**HIMETRIC**单位用于承载该复合控件的对话框资源。|  
|[CComCompositeControl::Create](#create)|调用此方法创建复合控件的控件窗口。|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|调用此方法以创建控制窗口，并告知任何托管的控件。|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|调用此方法以设置使用容器的背景色的复合控件的背景色。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|背景画笔。|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|当前具有焦点的窗口句柄。|  
  
## <a name="remarks"></a>备注  
 类派生自类`CComCompositeControl`继承 ActiveX 复合控件的功能。 ActiveX 控件派生自`CComCompositeControl`托管的标准对话框。 这些类型的控件称为复合控件，因为它们是能够托管其他控件 （本机 Windows 控件和 ActiveX 控件）。  
  
 `CComCompositeControl`标识可用于通过查找将被子类中的枚举的数据成员来创建复合控件的对话框资源。 此子类 IDD 成员设置为将用作该控件的窗口对话框资源的资源 ID。 以下是一种数据成员的类派生自的`CComCompositeControl`来标识要用于该控件的窗口的对话框资源应包含：  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  复合控件始终是有窗口控件，但可以包含无窗口控件。  
  
 控件由实现`CComCompositeControl`-派生的类具有默认按 tab 键生成的行为。 当在控件接收焦点，由正在选项卡式到包含应用程序中时，依次按 TAB 键将导致通过所有的复合控件的所含控件，然后出复合控件和到的下一项循环切换焦点容器的 tab 键顺序。 对托管控件的 tab 键顺序由对话框资源，并且确定的顺序将发生在哪些按 tab 键。  
  
> [!NOTE]
>  顺序一起正常工作的快捷键`CComCompositeControl`，需要将快捷键对应表加载为创建该控件，则传递的句柄和数回快捷键[IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，和在释放该控件时，最后销毁表。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap  
 调用此方法以建议或不建议由复合控件承载的所有控件。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>参数  
 `bAdvise`  
 如果所有控件都均可以收到通知; 则为 true否则为 false。  
  
### <a name="return-value"></a>返回值  
 `S_OK`  
 所有控件事件接收器映射已连接或从其事件源已成功断开连接。  
  
 **E_FAIL**  
 并非所有控制事件接收器映射无法连接或从其事件源已成功断开连接。  
  
 `E_POINTER`  
 此错误通常表示在控件的事件接收器映射的条目的问题或使用模板自变量中使用问题`IDispEventImpl`或`IDispEventSimpleImpl`基类。  
  
 **CONNECT_E_ADVISELIMIT**  
 连接点已达到其限制的连接，无法接受任何详细信息。  
  
 **CONNECT_E_CANNOTCONNECT**  
 接收器不支持通过此连接点所需的接口。  
  
 **CONNECT_E_NOCONNECTION**  
 Cookie 值不表示有效的连接。 此错误通常表示在控件的事件接收器映射的条目的问题或使用模板自变量中使用问题`IDispEventImpl`或`IDispEventSimpleImpl`基类。  
  
### <a name="remarks"></a>备注  
 此方法的基实现在事件接收器映射到这些条目搜索。 然后，它将建议或取消通知事件接收器映射的接收器项所描述的 COM 对象的连接点。 此成员方法还依赖于派生的类继承自的一个实例的事实`IDispEventImpl`的每个控件中将是建议还是 unadvised 接收器映射。  
  
##  <a name="calcextent"></a>CComCompositeControl::CalcExtent  
 调用此方法以计算的大小以**HIMETRIC**单位用于承载该复合控件的对话框资源。  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 对引用**大小**结构要填充此方法。  
  
### <a name="return-value"></a>返回值  
 如果该控件位于对话框; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 在中返回大小`size`参数。  
  
##  <a name="create"></a>CComCompositeControl::Create  
 调用此方法创建复合控件的控件窗口。  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 控件的父窗口的句柄。  
  
 `rcPos`  
 保留。  
  
 `dwInitParam`  
 在控件创建期间要传递给控件的数据。 数据作为传递`dwInitParam`将显示为**LPARAM**参数[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)消息，然后将其发送到复合控件时将会创建。  
  
### <a name="return-value"></a>返回值  
 新创建的复合控件对话框句柄。  
  
### <a name="remarks"></a>备注  
 此方法通常称为期间就地激活的控件。  
  
##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl  
 构造函数。  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>备注  
 初始化[CComCompositeControl::m_hbrBackground](#m_hbrbackground)和[CComCompositeControl::m_hWndFocus](#m_hwndfocus)为 NULL 的数据成员。  
  
##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl  
 析构函数。  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>备注  
 如果它存在，请删除背景对象。  
  
##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow  
 调用此方法以创建控制窗口，并告知任何托管的控件。  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 控件的父窗口的句柄。  
  
 `rcPos`  
 客户端中的复合控件的位置矩形坐标相对于`hWndParent`。  
  
### <a name="return-value"></a>返回值  
 返回新创建的复合控件对话框中的句柄。  
  
### <a name="remarks"></a>备注  
 此方法调用[CComCompositeControl::Create](#create)和[CComCompositeControl::AdviseSinkMap](#advisesinkmap)。  
  
##  <a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground  
 背景画笔。  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus  
 当前具有焦点的窗口句柄。  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient  
 调用此方法以设置使用容器的背景色的复合控件的背景色。  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)   
 [类概述](../../atl/atl-class-overview.md)
