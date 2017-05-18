---
title: "CComCompositeControl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ab99b8682e8b529cc124fbda1e6facaac48d0927
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 类
此类提供实现的复合控件所需的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要对您的复合控件的支持也从任何其他接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|构造函数。|  
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|调用此方法以建议或不建议由复合控件承载的所有控件。|  
|[CComCompositeControl::CalcExtent](#calcextent)|调用此方法来计算的大小以**HIMETRIC**对话框资源用来承载该复合控件的单元。|  
|[CComCompositeControl::Create](#create)|调用此方法来创建复合控件的控件窗口。|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|调用此方法以创建控制窗口并建议任何承载的控件。|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|调用此方法以设置使用容器的背景色的复合控件的背景色。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|背景画笔。|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|当前具有焦点的窗口句柄。|  
  
## <a name="remarks"></a>备注  
 从类派生的类`CComCompositeControl`继承 ActiveX 复合控件的功能。 ActiveX 控件派生自`CComCompositeControl`所承载的标准对话框。 这些类型的控件称为复合控件，因为它们是能够承载其他控件 （本机 Windows 控件和 ActiveX 控件）。  
  
 `CComCompositeControl`标识要用于通过查找的子类别中的枚举的数据成员创建复合控件的对话框资源。 IDD 这个子类别的成员设置为将用作控件的窗口对话框资源的资源 ID。 以下是此类派生自的数据成员的示例`CComCompositeControl`应包含来标识要用于控件的窗口的对话框资源︰  
  
 [!code-cpp[NVC_ATL_COM&#13;](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  复合控件始终是有窗口控件，但可以包含无窗口控件。  
  
 通过实现的控件`CComCompositeControl`的派生的类具有按 tab 键中内置的行为的默认值。 在控件中包含的应用程序移动到由接收焦点，连续按 TAB 键将导致循环遍历所有复合控件所含控件，然后出复合控件和容器的 tab 键顺序的下一项移焦点。 所承载的控件的 tab 键顺序由对话框资源、 确定的顺序将发生在哪个按 tab 键。  
  
> [!NOTE]
>  为了使一起正常工作的快捷键`CComCompositeControl`，就需要根据创建该控件加载快捷键对应表，则传递的句柄和恢复到的加速器数量[IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，和最后释放该控件时销毁表。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#14;](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap  
 调用此方法以建议或不建议由复合控件承载的所有控件。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>参数  
 `bAdvise`  
 如果所有控件都都可以收到通知; 则为 true否则为 false。  
  
### <a name="return-value"></a>返回值  
 `S_OK`  
 所有控件事件接收器映射已连接或从其事件源成功断开连接。  
  
 **E_FAIL**  
 并非所有控制事件接收器映射无法连接或从其事件源成功断开连接。  
  
 `E_POINTER`  
 此错误通常表示控件的事件接收器映射中的一项有问题或者在中使用的模板参数的问题`IDispEventImpl`或`IDispEventSimpleImpl`基类。  
  
 **CONNECT_E_ADVISELIMIT**  
 连接点已达到其限制的连接，无法接受任何更多。  
  
 **CONNECT_E_CANNOTCONNECT**  
 接收器不支持此连接点所需的接口。  
  
 **CONNECT_E_NOCONNECTION**  
 Cookie 值不表示有效的连接。 此错误通常表示控件的事件接收器映射中的一项有问题或者在中使用的模板参数的问题`IDispEventImpl`或`IDispEventSimpleImpl`基类。  
  
### <a name="remarks"></a>备注  
 此方法的基实现中搜索条目在事件接收器映射。 然后，它建议，或取消通知事件接收器映射接收器项所描述的 COM 对象的连接点。 此成员方法还依赖于在派生的类继承的一个实例的事实`IDispEventImpl`为每个控件在将是明智还是 unadvised 接收器映射。  
  
##  <a name="calcextent"></a>CComCompositeControl::CalcExtent  
 调用此方法来计算的大小以**HIMETRIC**对话框资源用来承载该复合控件的单元。  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 对引用**大小**填充此方法的结构。  
  
### <a name="return-value"></a>返回值  
 如果控件位于对话框; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 中返回大小`size`参数。  
  
##  <a name="create"></a>CComCompositeControl::Create  
 调用此方法来创建复合控件的控件窗口。  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 该控件的父窗口的句柄。  
  
 `rcPos`  
 保留。  
  
 `dwInitParam`  
 若要在控件创建期间传递到控件的数据。 数据作为传递`dwInitParam`将显示为**LPARAM**参数[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)消息，然后将其发送到复合控件获取在创建时。  
  
### <a name="return-value"></a>返回值  
 指向新建复合控件对话框中的句柄。  
  
### <a name="remarks"></a>备注  
 通常在就地激活控件的过程中调用此方法。  
  
##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl  
 构造函数。  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>备注  
 初始化[CComCompositeControl::m_hbrBackground](#m_hbrbackground)和[CComCompositeControl::m_hWndFocus](#m_hwndfocus)数据成员为 NULL。  
  
##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl  
 析构函数。  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>备注  
 背景对象存在时删除它。  
  
##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow  
 调用此方法以创建控制窗口并建议任何承载的控件。  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 该控件的父窗口的句柄。  
  
 `rcPos`  
 客户端中的复合控件的位置矩形坐标相对于`hWndParent`。  
  
### <a name="return-value"></a>返回值  
 新创建的复合控件对话框中返回的句柄。  
  
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

