---
title: IPropertyPageImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b07609b792b7080e2c4c432ed435381007ba286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075223"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl 类

此类实现`IUnknown`，并提供的默认实现[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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

|名称|描述|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPropertyPageImpl::Activate](#activate)|创建属性页对话框窗口。|
|[IPropertyPageImpl::Apply](#apply)|适用于通过指定的基础对象的属性页的当前值`SetObjects`。 ATL 实现返回 S_OK。|
|[IPropertyPageImpl::Deactivate](#deactivate)|销毁此窗口与创建`Activate`。|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|检索有关属性页的信息。|
|[IPropertyPageImpl::Help](#help)|调用属性页面的 Windows 帮助。|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|指示是否已更改的属性页，因为它已激活。|
|[IPropertyPageImpl::Move](#move)|定位并调整大小属性页对话框。|
|[IPropertyPageImpl::SetDirty](#setdirty)|标记为已更改或不变的属性页的状态。|
|[IPropertyPageImpl::SetObjects](#setobjects)|提供了一系列`IUnknown`与属性页关联的对象的指针。 这些对象接收当前的属性页值通过调用`Apply`。|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|提供的属性页`IPropertyPageSite`指针，通过该属性页与属性框架进行通信。|
|[IPropertyPageImpl::Show](#show)|使属性页对话框中可见或不可见。|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|处理指定的键击。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|指定是否在属性页的状态已更改。|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|存储与描述的属性页的文本字符串关联的资源标识符。|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|存储与属性页关联的帮助主题的上下文标识符。|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|存储与描述的属性页的帮助文件的名称关联的资源标识符。|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|将存储在属性页选项卡中显示的文本字符串与关联的资源标识符。|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|存储与属性页关联的对象数。|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|指向`IPropertyPageSite`通过其属性页与属性框架进行通信的接口。|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|指向数组的`IUnknown`与属性页关联的对象的指针。|
|[IPropertyPageImpl::m_size](#m_size)|存储的高度和宽度的属性页对话框中，以像素为单位。|

## <a name="remarks"></a>备注

[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)接口允许对象管理的属性表中的特定属性页面。 类`IPropertyPageImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="activate"></a>  IPropertyPageImpl::Activate

创建属性页对话框窗口。

```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>备注

默认情况下，对话框的始终是无模式，而不考虑的值*bModal*参数。

请参阅[IPropertyPage::Activate](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-activate) Windows SDK 中。

##  <a name="apply"></a>  IPropertyPageImpl::Apply

适用于通过指定的基础对象的属性页的当前值`SetObjects`。

```
HRESULT Apply();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IPropertyPage::Apply](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-apply) Windows SDK 中。

##  <a name="deactivate"></a>  IPropertyPageImpl::Deactivate

销毁对话框窗口使用创建[激活](#activate)。

```
HRESULT Deactivate();
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::Deactivate](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-deactivate) Windows SDK 中。

##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo

填充*pPageInfo*结构中的数据成员包含的信息。

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>备注

`GetPageInfo` 加载与关联的字符串资源[m_dwDocString](#m_dwdocstring)， [m_dwHelpFile](#m_dwhelpfile)，并[m_dwTitle](#m_dwtitle)。

请参阅[IPropertyPage::GetPageInfo](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) Windows SDK 中。

##  <a name="help"></a>  IPropertyPageImpl::Help

调用属性页面的 Windows 帮助。

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::Help](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-help) Windows SDK 中。

##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl

构造函数。

```
IPropertyPageImpl();
```

### <a name="remarks"></a>备注

初始化所有数据成员。

##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty

指示是否已更改的属性页，因为它已激活。

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>备注

`IsPageDirty` 如果页已更改，因为它已激活，则返回 S_OK。

##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty

指定是否在属性页的状态已更改。

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>  IPropertyPageImpl::m_nObjects

存储与属性页关联的对象数。

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>  IPropertyPageImpl::m_dwHelpContext

存储与属性页关联的帮助主题的上下文标识符。

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString

存储与描述的属性页的文本字符串关联的资源标识符。

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>  IPropertyPageImpl::m_dwHelpFile

存储与描述的属性页的帮助文件的名称关联的资源标识符。

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>  IPropertyPageImpl::m_dwTitle

将存储在属性页选项卡中显示的文本字符串与关联的资源标识符。

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite

指向[IPropertyPageSite](/windows/desktop/api/ocidl/nn-ocidl-ipropertypagesite)通过其属性页与属性框架进行通信的接口。

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>  IPropertyPageImpl::m_ppUnk

指向数组的`IUnknown`与属性页关联的对象的指针。

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>  IPropertyPageImpl::m_size

存储的高度和宽度的属性页对话框中，以像素为单位。

```
SIZE m_size;
```

##  <a name="move"></a>  IPropertyPageImpl::Move

定位并调整大小属性页对话框。

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::Move](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-move) Windows SDK 中。

##  <a name="setdirty"></a>  IPropertyPageImpl::SetDirty

标记为已更改或不变，具体取决于值的属性页的状态*bDirty*。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>参数

*bDirty*<br/>
[in]如果为 TRUE，则会将属性页的状态标记为已更改。 否则，它被标记为不变。

### <a name="remarks"></a>备注

如有必要，`SetDirty`通知属性页已更改的帧。

##  <a name="setobjects"></a>  IPropertyPageImpl::SetObjects

提供了一系列`IUnknown`与属性页关联的对象的指针。

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::SetObjects](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-setobjects) Windows SDK 中。

##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite

提供了与属性页[IPropertyPageSite](/windows/desktop/api/ocidl/nn-ocidl-ipropertypagesite)指针，通过该属性页与属性框架进行通信。

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::SetPageSite](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-setpagesite) Windows SDK 中。

##  <a name="show"></a>  IPropertyPageImpl::Show

使属性页对话框中可见或不可见。

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::Show](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-show) Windows SDK 中。

##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator

处理中指定的击键`pMsg`。

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>备注

请参阅[IPropertyPage::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) Windows SDK 中。

## <a name="see-also"></a>请参阅

[IPropertyPage2Impl 类](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
