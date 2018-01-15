---
title: "CWinFormsControl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs: C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2e6bf46cf28c3bca3d71f85cdd681745a0379bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl 类
提供用于承载 Windows 窗体控件的基本功能。  
  
## <a name="syntax"></a>语法  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### <a name="parameters"></a>参数  
 `TManagedControl`  
 要在 MFC 应用程序中显示一个.NET Framework Windows 窗体控件。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|将构造一个 MFC Windows 窗体控件包装对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|在 MFC 容器中创建 Windows 窗体控件。|  
|[CWinFormsControl::GetControl](#getcontrol)|检索指向 Windows 窗体控件的指针。|  
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|检索 Windows 窗体控件的句柄。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|替换[CWinFormsControl::GetControl](#getcontrol)表达式中。|  
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|将类型强制转换为指向 Windows 窗体控件。|  
  
## <a name="remarks"></a>备注  
 `CWinFormsControl`类提供用于承载 Windows 窗体控件的基本功能。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 MFC 代码不应缓存窗口句柄 (通常存储在`m_hWnd`)。 一些 Windows 窗体控件的属性需要基础 Win32`Window`被销毁，并且使用重新创建`DestroyWindow`和`CreateWindow`。 MFC Windows 窗体实现句柄`Destroy`和`Create`更新控件的事件的`m_hWnd`成员。  
  
> [!NOTE]
>  MFC Windows 窗体集成仅在动态链接 （在其中 AFXDLL 定义） 的 mfc 项目中可以正常工作。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxwinforms.h  
  
##  <a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl  
 在 MFC 容器中创建 Windows 窗体控件。  
  
```  
inline BOOL CreateManagedControl(
    System::Type^ pType,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID)  
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);

 
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    int nPlaceHolderID,  
    CWnd* pParentWnd);

 
inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);
```  
  
### <a name="parameters"></a>参数  
 `pType`  
 要创建控件的数据类型。 必须是[类型](https://msdn.microsoft.com/en-us/library/system.type)数据类型。  
  
 `dwStyle`  
 要应用于控件的窗口样式。 指定的组合[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 目前，支持仅以下样式： WS_TABSTOP、 WS_VISIBLE、 WS_DISABLED 和 WS_GROUP。  
  
 `rect`  
 A [RECT 结构](../../mfc/reference/rect-structure1.md)，它定义控件的左上角和右下角的坐标 （仅第一个重载）。  
  
 `nPlaceHolderID`  
 静态位置持有者控件的句柄放在资源编辑器中。 新创建的 Windows 窗体控件替换静态控件，假定其位置、 z 顺序和样式 （仅第二个重载）。  
  
 `pParentWnd`  
 指向父窗口的指针。  
  
 `nID`  
 要分配给新创建的控件的资源 ID 号。  
  
 `pControl`  
 Windows 窗体控件来与关联的实例[CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)对象 （仅适用于第四个重载）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回非零值。 如果不成功，则返回零。  
  
### <a name="remarks"></a>备注  
 此方法实例化 MFC 容器中的.NET Framework Windows 窗体控件。  
  
 方法的第一个重载接受的.NET Framework 数据类型`pType`以便 MFC 可以实例化此类型的新对象。 `pType`必须是[类型](https://msdn.microsoft.com/en-us/library/system.type)数据类型。  
  
 第二个重载的方法创建基于的 Windows 窗体控件`TManagedControl`的模板参数`CWinFormsControl`类。 大小和位置的控件基于`RECT`结构传递给方法。 仅`dwStyle`样式很重要。  
  
 方法的第三个重载创建替换静态控件，销毁它，并假设其位置、 z 顺序和样式的 Windows 窗体控件。 静态控件仅用作 Windows 窗体控件的占位符。 创建控件时，此重载将组合中的样式`dwStyle`与静态控件的资源样式。  
  
 方法的第四个重载允许您在已实例化 Windows 窗体控件中将传递`pControl`，MFC 将自动换行。 它必须与同一类型`TManagedControl`的模板参数`CWinFormsControl`类。  
  
 请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)的示例使用 Windows 窗体控件。  
  
##  <a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl  
 将构造一个 MFC Windows 窗体控件包装对象。  
  
```  
CWinFormsControl();
```  
  
### <a name="remarks"></a>备注  
 在调用时实例化 Windows 窗体控件[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。  
  
##  <a name="getcontrol"></a>CWinFormsControl::GetControl  
 检索指向 Windows 窗体控件的指针。  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向 Windows 窗体控件。  
  
### <a name="example"></a>示例  
  请参阅[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。  
  
##  <a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle  
 检索 Windows 窗体控件的句柄。  
  
```  
inline HWND GetControlHandle() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回 Windows 窗体控件的句柄。  
  
### <a name="remarks"></a>备注  
 `GetControlHandle`返回.NET Framework 的控件属性存储的窗口句柄的帮助器方法。 窗口句柄值复制到[CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd)到在呼叫期间[CWnd::Attach](../../mfc/reference/cwnd-class.md#attach)。  
  
##  <a name="operator_-_gt"></a>CWinFormsControl::operator-&gt;  
 替换[CWinFormsControl::GetControl](#getcontrol)表达式中。  
  
```  
inline TManagedControl^  operator->() const;  
```  
  
### <a name="remarks"></a>备注  
 此运算符提供了一种方便的语法，用于替换`GetControl`表达式中。  
  
 Windows 窗体上的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_tmanagedcontrol"></a>CWinFormsControl::operator TManagedControl ^  
 将类型强制转换为指向 Windows 窗体控件。  
  
```  
inline operator TManagedControl^() const;  
```  
  
### <a name="remarks"></a>备注  
 此运算符将传递`CWinFormsControl<TManagedControl>`接受指向 Windows 窗体控件的指针的函数。  
  
## <a name="see-also"></a>请参阅  
 [CWinFormsDialog 类](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)
