---
title: IDocHostUIHandlerDispatch 接口
ms.date: 11/04/2016
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 6ce3532e99dc1d0ff0151285766aa5d78c2b9e9d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421877"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 接口

Microsoft HTML 分析和呈现引擎的接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

> [!NOTE]
>  下表中的链接将指向的成员的 INet SDK 参考主题[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)接口。 `IDocHostUIHandlerDispatch` 具有相同的功能`IDocUIHostHandler`，使用不同的是，`IDocHostUIHandlerDispatch`是调度接口，而`IDocUIHostHandler`是自定义的接口。

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|从 MSHTML 实现调用[IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)。 也称为 MSHTML 显示模式 UI 时。|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|调用由 MSHTML 以允许主机替换 MSHTML 的数据对象在主机上。|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|当它被用作拖放目标以允许主机提供替代时，调用 MSHTML [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)。|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|由 MSHTML 获取主机的 IDispatch 接口调用。|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|检索 MSHTML 主机的用户界面功能。|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|返回 MSHTML 在其下存储用户首选项的注册表项。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|当 MSHTML 删除其菜单和工具栏时调用。|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|从 MSHTML 实现调用[IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)。|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|从 MSHTML 实现调用[ioleinplaceactiveobject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)。|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|从 MSHTML 实现调用[IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|从 MSHTML 以显示上下文菜单调用。|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允许主机替换 MSHTML 菜单和工具栏。|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|由 MSHTML 调用时[:: Translateaccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或[iolecontrolsite:: Translateaccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)调用。|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|由 MSHTML 以允许主机有机会修改要加载的 URL 调用。|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主机命令状态已更改。|

## <a name="remarks"></a>备注

主机可以替换菜单、 工具栏和上下文菜单通过实现此接口由 Microsoft HTML 分析和呈现引擎 (MSHTML)。

## <a name="requirements"></a>要求

此接口的定义现在以 IDL 或 c + +，如下所示。

|定义类型|文件|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h （也包括在 ATLBase.h）|

## <a name="see-also"></a>请参阅

[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)
