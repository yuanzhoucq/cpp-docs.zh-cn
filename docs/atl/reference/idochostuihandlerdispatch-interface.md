---
title: IDocHostUIHandlerDispatch 接口
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a9e672144160528e6a2fbfe4cb702c4d211ef720
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495909"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 接口

Microsoft HTML 分析和呈现引擎的接口。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

> [!NOTE]
>  下表中的链接指向[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))接口成员的 INet SDK 参考主题。 `IDocHostUIHandlerDispatch`具有与相同的功能`IDocUIHostHandler`, 不同之处在于, `IDocHostUIHandlerDispatch`它是一个调度`IDocUIHostHandler`接口, 而是一个自定义接口。

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|从[IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)的 MSHTML 实现中调用。 当 MSHTML 显示模式用户界面时也调用。|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|由 MSHTML 在主机上调用, 以允许主机替换 MSHTML 的数据对象。|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|当将其用作放置目标以允许主机提供替代的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)时, 由 MSHTML 调用。|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|由 MSHTML 调用以获取主机的 IDispatch 接口。|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|检索 MSHTML 主机的 UI 功能。|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|返回 MSHTML 用于存储用户首选项的注册表项。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|当 MSHTML 删除其菜单和工具栏时调用。|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|从[IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)的 MSHTML 实现中调用。|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|从[IOleInPlaceActiveObject:: onframewindowactivate 调用](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)的 MSHTML 实现中调用。|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|从[IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)的 MSHTML 实现中调用。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|从 MSHTML 调用以显示上下文菜单。|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允许主机替换 MSHTML 菜单和工具栏。|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|调用[IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或[IOleControlSite:: TRANSLATEACCELERATOR](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)时由 MSHTML 调用。|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|由 MSHTML 调用, 以允许主机有机会修改要加载的 URL。|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主机命令状态已更改。|

## <a name="remarks"></a>备注

宿主可以通过实现此接口来替换 Microsoft HTML 分析和呈现引擎 (MSHTML) 使用的菜单、工具栏和上下文菜单。

## <a name="requirements"></a>要求

此接口的定义以 IDL 或C++的形式提供, 如下所示。

|定义类型|文件|
|---------------------|----------|
|.IDL|ATLIFace.idl|
|C++|ATLIFace (也包含在 Atlbase.h 中)|

## <a name="see-also"></a>请参阅

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
