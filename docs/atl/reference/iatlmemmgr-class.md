---
title: IAtlMemMgr 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35cc685c06eaa3992ec8444cfc5d99f2191145a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366203"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 类
此类表示为内存管理器的接口。  
  
## <a name="syntax"></a>语法  
  
```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[分配](#allocate)|调用此方法来分配内存块。|  
|[可用](#free)|调用此方法以释放的内存块。|  
|[GetSize](#getsize)|调用此方法来检索分配的内存块的大小。|  
|[重新分配](#reallocate)|调用此方法以重新分配的内存块。|  
  
## <a name="remarks"></a>备注  
 此接口由实现[CComHeap](../../atl/reference/ccomheap-class.md)， [CCRTHeap](../../atl/reference/ccrtheap-class.md)， [CLocalHeap](../../atl/reference/clocalheap-class.md)， [CGlobalHeap](../../atl/reference/cglobalheap-class.md)，或[CWin32Heap](../../atl/reference/cwin32heap-class.md).  
  
> [!NOTE]
>  本地和全局堆函数慢于其他内存管理函数，并且未提供尽可能多的功能。 因此，新的应用程序应使用[堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 这些是位于[CWin32Heap](../../atl/reference/cwin32heap-class.md)类。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** atlmem.h  
  
##  <a name="allocate"></a>  IAtlMemMgr::Allocate  
 调用此方法来分配内存块。  
  
```
void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 新内存块中请求的字节数。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配内存块的起始位置。  
  
### <a name="remarks"></a>备注  
 调用[IAtlMemMgr::Free](#free)或[IAtlMemMgr::Reallocate](#reallocate)来释放由此方法分配的内存。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[IAtlMemMgr 概述](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="free"></a>  IAtlMemMgr::Free  
 调用此方法以释放的内存块。  
  
```
void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。  
  
### <a name="remarks"></a>备注  
 使用此方法来释放内存通过获取[IAtlMemMgr::Allocate](#allocate)或[IAtlMemMgr::Reallocate](#reallocate)。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[IAtlMemMgr 概述](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="getsize"></a>  IAtlMemMgr::GetSize  
 调用此方法来检索分配的内存块的大小。  
  
```
size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。  
  
### <a name="return-value"></a>返回值  
 返回以字节为单位的内存块的大小。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[IAtlMemMgr 概述](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate  
 调用此方法以重新分配由该内存管理器分配的内存。  
  
```
void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。  
  
 `nBytes`  
 新内存块中请求的字节数。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配内存块的起始位置。  
  
### <a name="remarks"></a>备注  
 调用[IAtlMemMgr::Free](#free)或[IAtlMemMgr::Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 从概念上讲此方法释放现有内存，并分配新内存块。 实际上，可能会扩展或否则重用现有的内存。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[IAtlMemMgr 概述](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu  
 **AllowContextMenu**属性指定是否允许所承载的控件以显示上下文菜单。  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>参数  
 *pbAllowContextMenu*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI  
 **AllowShowUI**属性指定是否允许所承载的控件以显示其自身用户界面。  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>参数  
 *pbAllowShowUI*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 **AllowWindowlessActivation**属性指定容器是否允许无窗口激活。  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>参数  
 *pbAllowWindowless*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor  
 `BackColor`属性指定的容器的环境背景色。  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>参数  
 *pclrBackground*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**COLOR_BTNFACE**或**COLOR_WINDOW**作为 （具体取决于主机窗口的父级是否对话框） 此属性的默认值。  
  
##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault**是允许控件查看它是否默认控件的环境属性。  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>参数  
 *pbDisplayAsDefault*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags**属性指定应发生以响应一次双击该操作。  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>参数  
 *pdwDocHostDoubleClickFlags*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**DOCHOSTUIDBLCLK_DEFAULT**作为此属性的默认值。  
  
##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags  
 **DocHostFlags**属性指定该主机对象的用户界面功能。  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>参数  
 *pdwDocHostFlags*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**DOCHOSTUIFLAG_NO3DBORDER**作为此属性的默认值。  
  
##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font  
 **字体**属性指定的容器的环境的字体。  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 [out]地址**IFontDisp**用来接收此属性的当前值的接口指针。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现此属性的默认值中用作默认 GUI 字体或系统字体。  
  
##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor  
 `ForeColor`属性指定的容器的环境前景色。  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>参数  
 *pclrForeground*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用此属性的默认值作为系统窗口文本颜色。  
  
##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID  
 **LocaleID**属性指定的容器的环境的区域设置 ID。  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>参数  
 *plcidLocaleID*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用此属性的默认值作为用户的默认区域设置。  
  
 使用此方法可以发现环境 LocalID，也就是说，该程序的 LocaleID 控件中正在使用。 一旦你知道 LocaleID，可以从资源文件或附属 DLL，依此类推调用代码以加载特定于区域设置标题，错误消息文本。  
  
##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect  
 **MessageReflect**环境属性指定容器是否将反映到托管控件的消息。  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>参数  
 *pbMessageReflect*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath  
 **OptionKeyPath**属性指定对用户设置的注册表项路径。  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>参数  
 *pbstrOptionKeyPath*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles  
 **ShowGrabHandles**环境属性允许要查找是否它应绘制本身使用抓取句柄的控件。  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>参数  
 *pbShowGrabHandles*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现始终返回**VARIANT_FALSE**作为此属性的值。  
  
##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching  
 **ShowHatching**环境属性使控件可以了解是否它应绘制自身阴影线。  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>参数  
 *pbShowHatching*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现始终返回**VARIANT_FALSE**作为此属性的值。  
  
##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode  
 **UserMode**属性指定的容器的环境的用户模式。  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>参数  
 *pbUserMode*  
 [out]要接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu  
 **AllowContextMenu**属性指定是否允许所承载的控件以显示上下文菜单。  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>参数  
 *bAllowContextMenu*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI  
 **AllowShowUI**属性指定是否允许所承载的控件以显示其自身用户界面。  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>参数  
 *bAllowShowUI*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 **AllowWindowlessActivation**属性指定容器是否允许无窗口激活。  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>参数  
 *bAllowWindowless*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor  
 `BackColor`属性指定的容器的环境背景色。  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>参数  
 *clrBackground*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**COLOR_BTNFACE**或**COLOR_WINDOW**作为 （具体取决于主机窗口的父级是否对话框） 此属性的默认值。  
  
##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault**是允许控件查看它是否默认控件的环境属性。  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>参数  
 `bDisplayAsDefault`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags**属性指定应发生以响应一次双击该操作。  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>参数  
 *dwDocHostDoubleClickFlags*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**DOCHOSTUIDBLCLK_DEFAULT**作为此属性的默认值。  
  
##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags  
 **DocHostFlags**属性指定该主机对象的用户界面功能。  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>参数  
 *dwDocHostFlags*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用**DOCHOSTUIFLAG_NO3DBORDER**作为此属性的默认值。  
  
##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font  
 **字体**属性指定的容器的环境的字体。  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现此属性的默认值中用作默认 GUI 字体或系统字体。  
  
##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor  
 `ForeColor`属性指定的容器的环境前景色。  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>参数  
 *clrForeground*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用此属性的默认值作为系统窗口文本颜色。  
  
##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID  
 **LocaleID**属性指定的容器的环境的区域设置 ID。  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>参数  
 *lcidLocaleID*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用此属性的默认值作为用户的默认区域设置。  
  
##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect  
 **MessageReflect**环境属性指定容器是否将反映到托管控件的消息。  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>参数  
 `bMessageReflect`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath  
 **OptionKeyPath**属性指定对用户设置的注册表项路径。  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>参数  
 *bstrOptionKeyPath*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode  
 **UserMode**属性指定的容器的环境的用户模式。  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>参数  
 `bUserMode`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch  
 调用此方法来补充具有用户定义的接口的默认环境属性接口。  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>参数  
 *pDispatch*  
 指向新的接口指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 当`SetAmbientDispatch`调用使用到新接口指针，此新界面将用于调用任何属性或请求的托管控件的方法-如果这些属性没有已提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl  
 将现有 （和以前初始化） 的控件附加到该主机对象，使用由窗口`hWnd`。  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 *pUnkControl*  
 [in]指向的指针**IUnknown**要附加到该主机对象的控件的接口。  
  
 `hWnd`  
 [in]要用于承载窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl  
 创建控件，初始化它，并在标识窗口中承载它`hWnd`。  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>参数  
 `lpTricsData`  
 [in]标识要创建的控件的字符串。 可以是 （必须包括大括号） 的 CLSID、 ProgID，URL 或原始 HTML (前缀**MSHTML:**)。  
  
 `hWnd`  
 [in]要用于承载窗口的句柄。  
  
 `pStream`  
 [in]包含控件的初始化数据的流接口指针。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 此窗口将公开此接口，以便消息可以发射到控件和其他容器功能将使用该主机对象通过子类化。  
  
 调用此方法等效于调用[IAxWinHostWindow::CreateControlEx](#createcontrolex)。  
  
 若要创建授权的 ActiveX 控件，请参阅[IAxWinHostWindowLic::CreateControlLic](#createcontrollicex)。  
  
##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx  
 创建 ActiveX 控件，初始化它，并在指定窗口，类似于中承载它[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 `lpTricsData`  
 [in]标识要创建的控件的字符串。 可以是 （必须包括大括号） 的 CLSID、 ProgID，URL 或原始 HTML (前缀为**MSHTML:**)。  
  
 `hWnd`  
 [in]要用于承载窗口的句柄。  
  
 `pStream`  
 [in]包含控件的初始化数据的流接口指针。 可以是**NULL**。  
  
 `ppUnk`  
 [out]将接收的指针的地址**IUnknown**接口创建的控件。 可以是**NULL**。  
  
 *riidAdvise*  
 [in]包含的对象上的传出接口的接口标识符。 可以是**IID_NULL**。  
  
 *punkAdvise*  
 [in]指向的指针**IUnknown**要连接到指定的包含对象上的连接点的接收器对象的接口`iidSink`。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 与不同`CreateControl`方法，`CreateControlEx`还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。  
  
 若要创建授权的 ActiveX 控件，请参阅[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)。  
  
##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl  
 返回由所承载的控件的指定的接口指针。  
  
```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `riid`  
 [in]所请求的控件上某个接口 ID。  
  
 `ppvObject`  
 [out]将收到创建的控件的指定的接口的指针的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch  
 设置可供通过所含控件的外部调度接口[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>参数  
 `pDisp`  
 [in]指向的指针`IDispatch`接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler  
 调用此函数可设置外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)接口`CAxWindow`对象。  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>参数  
 `pDisp`  
 [in]指向的指针**IDocHostUIHandlerDispatch**接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 此函数可供查询主机的站点的控件 （如 Web 浏览器控件）`IDocHostUIHandlerDispatch`接口。  
  
##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic  
 创建授权的控件，初始化它，并在标识窗口中承载它`hWnd`。  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>参数  
 `bstrLic`  
 [in]BSTR，其中包含该控件的许可证密钥。  
  
### <a name="remarks"></a>备注  
 请参阅[IAxWinHostWindow::CreateControl](#createcontrol)有关的剩余的参数和返回值的说明。  
  
 调用此方法等效于调用[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 创建授权的 ActiveX 控件，初始化它，并在指定窗口，类似于中承载它[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 `bstrLic`  
 [in]BSTR，其中包含该控件的许可证密钥。  
  
### <a name="remarks"></a>备注  
 请参阅[IAxWinHostWindow::CreateControlEx](#createcontrolex)有关的剩余的参数和返回值的说明。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`IAxWinHostWindowLic::CreateControlLicEx`。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
