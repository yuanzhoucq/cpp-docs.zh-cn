---
title: IDocHostUIHandlerDispatch 接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 936d9b30f18f5ef84c68c55a1607cfcd88d45525
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884608"
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
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|从 MSHTML 实现调用[IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115)。 也称为 MSHTML 显示模式 UI 时。|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|调用由 MSHTML 以允许主机替换 MSHTML 的数据对象在主机上。|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|当它被用作拖放目标以允许主机提供替代时，调用 MSHTML [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|由 MSHTML 获取主机的 IDispatch 接口调用。|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|检索 MSHTML 主机的用户界面功能。|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|返回 MSHTML 在其下存储用户首选项的注册表项。|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|当 MSHTML 删除其菜单和工具栏时调用。|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|从 MSHTML 实现调用[IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)。|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|从 MSHTML 实现调用[ioleinplaceactiveobject:: Onframewindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)。|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|从 MSHTML 实现调用[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)。|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|从 MSHTML 以显示上下文菜单调用。|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|允许主机替换 MSHTML 菜单和工具栏。|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|由 MSHTML 调用时[:: Translateaccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)或[iolecontrolsite:: Translateaccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756)调用。|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|由 MSHTML 以允许主机有机会修改要加载的 URL 调用。|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|通知主机命令状态已更改。|  
  
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









