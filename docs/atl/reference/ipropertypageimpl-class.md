---
title: IPropertyPageImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 154bfb5beb258ff26649f44f0bd4c23fb8708977
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745864"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl 类

此类实现`IUnknown`并提供[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)接口的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPropertyPageImpl`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[I属性页页：：I属性页页](#ipropertypageimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IPropertyPageimpl：：激活](#activate)|为属性页创建对话框窗口。|
|[IPropertypage：应用](#apply)|将当前属性页值应用于通过`SetObjects`指定的基础对象。 ATL 实现返回S_OK。|
|[IPropertyPageimpl：:D激活](#deactivate)|销毁使用`Activate`创建的窗口。|
|[IPropertyPageimpl：：获取Pageinfo](#getpageinfo)|检索有关属性页的信息。|
|[IPropertyPageimpl：：帮助](#help)|调用属性页的 Windows 帮助。|
|[I属性页页：：是页面脏](#ispagedirty)|指示属性页自激活以来是否已更改。|
|[I属性页页：移动](#move)|定位属性页对话框并调整大小。|
|[I属性页页：：设置脏](#setdirty)|将属性页的状态标记为已更改或未更改。|
|[IPropertypageimpl：：设置对象](#setobjects)|为与属性页`IUnknown`关联的对象提供指针数组。 这些对象通过调用`Apply`接收当前属性页值。|
|[I属性页页：：设置页面网站](#setpagesite)|使用`IPropertyPageSite`指针向属性页提供，属性页通过该指针与属性框架通信。|
|[IPropertyPageimpl：：显示](#show)|使属性页对话框可见或不可见。|
|[IPropertyPageimpl：：翻译加速器](#translateaccelerator)|处理指定的击键。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[IPropertyPageimpl：：m_bDirty](#m_bdirty)|指定属性页的状态是否已更改。|
|[IPropertyPageimpl：：m_dwDocString](#m_dwdocstring)|存储与描述属性页的文本字符串关联的资源标识符。|
|[IPropertyPageimpl：：m_dwHelpContext](#m_dwhelpcontext)|存储与属性页关联的帮助主题的上下文标识符。|
|[IPropertyPageimpl：m_dwHelpFile](#m_dwhelpfile)|存储与描述属性页的帮助文件的名称关联的资源标识符。|
|[IPropertyPageimpl：：m_dwTitle](#m_dwtitle)|存储与显示在属性页的选项卡中的文本字符串关联的资源标识符。|
|[IPropertyPageimpl：：m_nObjects](#m_nobjects)|存储与属性页关联的对象数。|
|[IPropertyPageimpl：：m_pPageSite](#m_ppagesite)|指向属性页`IPropertyPageSite`通过该接口与属性框架通信的接口。|
|[IPropertypage：m_ppUnk](#m_ppunk)|指向指向与属性页`IUnknown`关联的对象的指针数组。|
|[IPropertyPageimpl：：m_size](#m_size)|存储属性页对话框的高度和宽度（以像素为单位）。|

## <a name="remarks"></a>备注

[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)接口允许对象管理属性表中的特定属性页。 类`IPropertyPageImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageimpl：：激活

为属性页创建对话框窗口。

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>备注

默认情况下，无论*bModal*参数的值如何，对话框始终处于无模式状态。

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate)Windows SDK 中激活。

## <a name="ipropertypageimplapply"></a><a name="apply"></a>IPropertypage：应用

将当前属性页值应用于通过`SetObjects`指定的基础对象。

```
HRESULT Apply();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IPropertyPage：：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply)Windows SDK 中应用。

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageimpl：:D激活

销毁使用[激活](#activate)创建的对话框窗口。

```
HRESULT Deactivate();
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：:D在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate)Windows SDK 中激活。

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageimpl：：获取Pageinfo

使用数据成员中包含的信息填充*pPageInfo*结构。

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>备注

`GetPageInfo`加载与[m_dwDocString、m_dwHelpFile](#m_dwdocstring)和[m_dwTitle](#m_dwtitle)关联的[m_dwHelpFile](#m_dwhelpfile)字符串资源。

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo)Windows SDK 中获取Pageinfo。

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageimpl：：帮助

调用属性页的 Windows 帮助。

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：Windows](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) SDK 中的帮助。

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>I属性页页：：I属性页页

构造函数。

```
IPropertyPageImpl();
```

### <a name="remarks"></a>备注

初始化所有数据成员。

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>I属性页页：：是页面脏

指示属性页自激活以来是否已更改。

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>备注

`IsPageDirty`如果页面自激活以来已更改，则返回S_OK。

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageimpl：：m_bDirty

指定属性页的状态是否已更改。

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageimpl：：m_nObjects

存储与属性页关联的对象数。

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageimpl：：m_dwHelpContext

存储与属性页关联的帮助主题的上下文标识符。

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageimpl：：m_dwDocString

存储与描述属性页的文本字符串关联的资源标识符。

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageimpl：m_dwHelpFile

存储与描述属性页的帮助文件的名称关联的资源标识符。

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageimpl：：m_dwTitle

存储与显示在属性页的选项卡中的文本字符串关联的资源标识符。

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageimpl：：m_pPageSite

指向[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)界面，属性页通过该接口与属性框架通信。

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertypage：m_ppUnk

指向指向与属性页`IUnknown`关联的对象的指针数组。

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageimpl：：m_size

存储属性页对话框的高度和宽度（以像素为单位）。

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>I属性页页：移动

定位属性页对话框并调整大小。

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move)Windows SDK 中移动。

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>I属性页页：：设置脏

根据*bDirty*的值，将属性页的状态标记为已更改或未更改。

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>参数

*bDirty*<br/>
[在]如果为 TRUE，则属性页的状态将标记为已更改。 否则，它将标记为未更改。

### <a name="remarks"></a>备注

如有必要，`SetDirty`通知框架属性页已更改。

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>IPropertypageimpl：：设置对象

为与属性页`IUnknown`关联的对象提供指针数组。

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects)Windows SDK 中设置对象。

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>I属性页页：：设置页面网站

使用[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)指针提供属性页，属性页通过该指针与属性框架通信。

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite)Windows SDK 中设置PageSite。

## <a name="ipropertypageimplshow"></a><a name="show"></a>IPropertyPageimpl：：显示

使属性页对话框可见或不可见。

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show)Windows SDK 中显示。

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageimpl：：翻译加速器

处理 中`pMsg`指定的击键。

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage：在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator)Windows SDK 中翻译加速器。

## <a name="see-also"></a>请参阅

[IPropertyPage2Impl 类](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
