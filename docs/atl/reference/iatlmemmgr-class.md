---
title: IAtlMemMgr 类
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: fcecf716e9d865b1b8590a733216576e0da4c2fb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746013"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 类

此类表示内存管理器的接口。

## <a name="syntax"></a>语法

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[分配](#allocate)|调用此方法来分配内存块。|
|[免费](#free)|调用此方法以释放内存块。|
|[GetSize](#getsize)|调用此方法以检索已分配内存块的大小。|
|[重新分配](#reallocate)|调用此方法以重新分配内存块。|

## <a name="remarks"></a>备注

此接口由 CComHeap、CCRTHeap、CLocalHeap、CGlobalHeap 或[CWin32Heap](../../atl/reference/cwin32heap-class.md)实现。 [CComHeap](../../atl/reference/ccomheap-class.md) [CCRTHeap](../../atl/reference/ccrtheap-class.md) [CLocalHeap](../../atl/reference/clocalheap-class.md) [CGlobalHeap](../../atl/reference/cglobalheap-class.md)

> [!NOTE]
> 本地堆和全局堆函数比其他内存管理函数慢，并且不提供尽可能多的功能。 因此，新应用程序应使用[堆函数](/windows/win32/Memory/heap-functions)。 这些在[CWin32Heap](../../atl/reference/cwin32heap-class.md)类中可用。

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>要求

**标题：** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr：分配

调用此方法来分配内存块。

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*n 字节*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[IAtlMemMgr：：免费](#free)或[IAtlMemMgr：重新分配](#reallocate)以释放此方法分配的内存。

### <a name="example"></a>示例

例如，请参阅[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr：免费

调用此方法以释放内存块。

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。

### <a name="remarks"></a>备注

使用此方法释放[IAtlMemMgr](#allocate)获得的内存：：分配或[IAtlMemmgr：：重新分配](#reallocate)。

### <a name="example"></a>示例

例如，请参阅[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr：获取Size

调用此方法以检索已分配内存块的大小。

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。

### <a name="return-value"></a>返回值

返回内存块的大小（以字节为单位）。

### <a name="example"></a>示例

例如，请参阅[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr：重新分配

调用此方法以重新分配由该内存管理器分配的内存。

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。

*n 字节*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[IAtlMemMgr：：免费](#free)或[IAtlMemMgr：重新分配](#reallocate)以释放此方法分配的内存。

从概念上讲，此方法会释放现有内存并分配新的内存块。 实际上，现有内存可能会扩展或以其他方式重用。

### <a name="example"></a>示例

例如，请参阅[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWin 环境调度：：get_AllowContextMenu

属性`AllowContextMenu`指定是否允许托管控件显示其自己的上下文菜单。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>参数

*pbAllow 上下文菜单*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWin 环境调度：：get_AllowShowUI

该`AllowShowUI`属性指定是否允许托管控件显示其自己的用户界面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>参数

*pbAllowShowUI*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWin 环境调度：：get_AllowWindowlessActivation

属性`AllowWindowlessActivation`指定容器是否允许无窗口激活。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>参数

*pbAllow 无窗口*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWin 环境调度：：get_BackColor

属性`BackColor`指定容器的环境背景颜色。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>参数

*pclr背景*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用COLOR_BTNFACE或COLOR_WINDOW作为此属性的默认值（取决于主机窗口的父对象是否是对话框）。

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWin 环境调度：：get_DisplayAsDefault

`DisplayAsDefault`是一个环境属性，允许控件找出它是默认控件。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>参数

*pb 显示AsDefault*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWin 环境调度：：get_DocHostDoubleClickFlags

属性`DocHostDoubleClickFlags`指定响应双击而应执行的操作。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>参数

*pdwDocHost双击标志*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIDBLCLK_DEFAULT作为此属性的默认值。

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWin 环境调度：：get_DocHostFlags

该`DocHostFlags`属性指定主机对象的用户界面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>参数

*pdwDocHostFlags*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIFLAG_NO3DBORDER作为此属性的默认值。

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWin 环境调度：：get_Font

属性`Font`指定容器的环境字体。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
[出]用于接收此属性的`IFontDisp`当前值的接口指针的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用默认 GUI 字体或系统字体作为此属性的默认值。

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWin 环境调度：：get_ForeColor

属性`ForeColor`指定容器的环境前景颜色。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>参数

*pclr前景*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用系统窗口文本颜色作为此属性的默认值。

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWin 环境调度：：get_LocaleID

属性`LocaleID`指定容器的环境区域设置 ID。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>参数

*plcidLocaleID*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用用户的默认区域设置作为此属性的默认值。

使用此方法，您可以发现环境局部 ID，即控件正在使用的程序的 LocaleID。 了解区域设置ID后，可以调用代码从资源文件或附属 DLL 加载特定于区域设置的标题、错误消息文本等。

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWin 环境调度：：get_MessageReflect

环境`MessageReflect`属性指定容器是否将消息反映到托管控件。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>参数

*pbMessage 反射*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWin 环境调度：：get_OptionKeyPath

该`OptionKeyPath`属性指定用户设置的注册表键路径。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>参数

*pbstrOptionKeyPath*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWin 环境调度：：get_ShowGrabHandles

环境`ShowGrabHandles`属性允许控件找出是否应使用抓取手柄绘制自身。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>参数

*pbShowGrabHandles*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现始终返回VARIANT_FALSE作为此属性的值。

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWin 环境调度：：get_ShowHatching

环境`ShowHatching`属性允许控件找出是否应绘制自身阴影。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>参数

*pbShowHatching*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现始终返回VARIANT_FALSE作为此属性的值。

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWin 环境调度：：get_UserMode

该`UserMode`属性指定容器的环境用户模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>参数

*pbUser 模式*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxwin 环境调度：:put_允许上下文菜单

属性`AllowContextMenu`指定是否允许托管控件显示其自己的上下文菜单。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>参数

*bAllowContext菜单*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWin 环境调度：:put_允许ShowUI

该`AllowShowUI`属性指定是否允许托管控件显示其自己的用户界面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>参数

*bAllowShowUI*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxwin 环境调度：:put_允许无窗口激活

属性`AllowWindowlessActivation`指定容器是否允许无窗口激活。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>参数

*bAllow 无窗口*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWin 环境调度：:put_背面颜色

属性`BackColor`指定容器的环境背景颜色。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>参数

*clrBackground*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用COLOR_BTNFACE或COLOR_WINDOW作为此属性的默认值（取决于主机窗口的父对象是否是对话框）。

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWin 环境调度：:put_显示作为默认

`DisplayAsDefault`是一个环境属性，允许控件找出它是默认控件。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>参数

*b 显示默认*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxwin 环境调度：:put_DocHost 双键单击标志

属性`DocHostDoubleClickFlags`指定响应双击而应执行的操作。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>参数

*dwDocHost双击标志*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIDBLCLK_DEFAULT作为此属性的默认值。

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWin 环境调度：:put_DocHostFlags

该`DocHostFlags`属性指定主机对象的用户界面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>参数

*dwDocHostFlags*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIFLAG_NO3DBORDER作为此属性的默认值。

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWin 环境调度：:put_Font

属性`Font`指定容器的环境字体。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用默认 GUI 字体或系统字体作为此属性的默认值。

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWin 环境调度：:put_ForeColor

属性`ForeColor`指定容器的环境前景颜色。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>参数

*clr前景*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用系统窗口文本颜色作为此属性的默认值。

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWin 环境调度：:put_localeID

属性`LocaleID`指定容器的环境区域设置 ID。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>参数

*lcidLocaleID*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用用户的默认区域设置作为此属性的默认值。

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWin 环境调度：:put_消息反射

环境`MessageReflect`属性指定容器是否将消息反映到托管控件。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>参数

*b消息反射*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWin 环境调度：:put_选项关键路径

该`OptionKeyPath`属性指定用户设置的注册表键路径。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>参数

*bstrOptionKeyPath*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWin 环境调度：:put_用户模式

该`UserMode`属性指定容器的环境用户模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>参数

*用户模式*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxwin 环境调度Ex：：设置环境调度

调用此方法是为了使用用户定义的接口补充默认环境属性接口。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>参数

*pDispatch*<br/>
指向新接口的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

当`SetAmbientDispatch`使用指向新接口的指针调用时，此新接口将用于调用托管控件要求的任何属性或方法 - 如果这些属性尚未由[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)提供。

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHost 窗口：：附加控制

使用*hWnd*标识的窗口将现有（以前初始化）控件附加到主机对象。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>参数

*pUnkControl*<br/>
[在]指向要附加到主机`IUnknown`对象的控件接口的指针。

*hwnd*<br/>
[在]用于托管的窗口的句柄。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHost 窗口：：创建控制

创建控件，初始化它，并将其托管在*hWnd*标识的窗口中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>参数

*lpTricsData*<br/>
[在]标识要创建的控件的字符串。 可以是 CLSID（必须包括大括号）、ProgID、URL 或原始 HTML（由**MSHTML**预缀： 。

*hwnd*<br/>
[在]用于托管的窗口的句柄。

*pStream*<br/>
[在]包含控件初始化数据的流的接口指针。 可以为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此窗口将由公开此接口的主机对象进行子分类，以便消息可以反射到控件，其他容器功能将起作用。

调用此方法等效于调用[IAxWinHostWindow：：createControlEx](#createcontrolex)。

要创建许可的 ActiveX 控件，请参阅[IAxWinHostWindowlic：：创建控制项](#createcontrollicex)。

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHost 窗口：：创建控制Ex

创建一个 ActiveX 控件，初始化它，并将其托管在指定的窗口中，类似于[IAxWinHostWindow：：创建控制](#createcontrol)。

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>参数

*lpTricsData*<br/>
[在]标识要创建的控件的字符串。 可以是 CLSID（必须包括大括号）、ProgID、URL 或原始 HTML（与**MSHTML**一起预缀： 。

*hwnd*<br/>
[在]用于托管的窗口的句柄。

*pStream*<br/>
[在]包含控件初始化数据的流的接口指针。 可以为 NULL。

*普恩克*<br/>
[出]将接收创建控件接口`IUnknown`的指针的地址。 可以为 NULL。

*里德建议*<br/>
[在]包含对象上传出接口的接口标识符。 可以IID_NULL。

*朋克建议*<br/>
[在]指向要连接到`IUnknown`所指定包含对象的连接点的接收器对象的接口的`iidSink`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

与`CreateControl`方法不同`CreateControlEx`，还允许您接收指向新创建的控件的接口指针，并设置事件接收器以接收控件触发的事件。

要创建许可的 ActiveX 控件，请参阅[IAxWinHostWindowlic：：创建控制项](#createcontrollicex)。

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHost 窗口：：查询控制

返回托管控件提供的指定接口指针。

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>参数

*riid*<br/>
[在]请求的控件上的接口的 ID。

*ppvObject*<br/>
[出]将接收已创建控件的指定接口的指针的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHost 窗口：：设置外部调度

设置外部接口，可通过[IDocHostUIHandlerDispatch：get 外部](../../atl/reference/idochostuihandlerdispatch-interface.md)方法包含控件。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
[在]指向接口的`IDispatch`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHost 窗口：：设置外部 UIHandler

调用此函数以设置`CAxWindow`对象的外部[IDocHostUIHandlerDispatch 接口](../../atl/reference/idochostuihandlerdispatch-interface.md)。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
[在]指向接口的`IDocHostUIHandlerDispatch`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此函数由查询主机站点的`IDocHostUIHandlerDispatch`接口的控件（如 Web 浏览器控件）使用。

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostwindowlic：：创建控制

创建许可控件，初始化它，并将其托管在 标识的`hWnd`窗口中。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>参数

*bstrLIC*<br/>
[在]包含控件的许可证密钥的 BSTR。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[IAxWinHostWindow：创建控制](#createcontrol)。

调用此方法等效于调用[IAxWinHostWindowlic：：创建控制](#createcontrollicex)

### <a name="example"></a>示例

有关 使用`IAxWinHostWindowLic::CreateControlLic`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHost窗口：：创建控制

创建许可的 ActiveX 控件，初始化它，并将其托管在指定的窗口中，类似于[IAxWinHostWindow：：创建控制](#createcontrol)。

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>参数

*bstrLIC*<br/>
[在]包含控件的许可证密钥的 BSTR。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[IAxWinHostWindow：创建ControlEx。](#createcontrolex)

### <a name="example"></a>示例

有关 使用`IAxWinHostWindowLic::CreateControlLicEx`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
