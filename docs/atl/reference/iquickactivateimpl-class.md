---
title: IQuickActivateImpl 类
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329557"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 类

此类将容器的控制初始化合并为单个调用。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IQuickActivateImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I快速激活：：获取内容范围](#getcontentextent)|检索正在运行的控件的当前显示大小。|
|[I 快速激活：：快速激活](#quickactivate)|对正在加载的控件执行快速初始化。|
|[I快速激活：：设置内容范围](#setcontentextent)|通知容器为其分配的显示空间的控件。|

## <a name="remarks"></a>备注

[IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate)接口通过在单个调用中合并初始化，帮助容器在加载控件时避免延迟。 该方法`QuickActivate`允许容器传递指向[QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer)结构的指针，该结构包含指向控件需要的所有接口的指针。 返回时，控件将指针传回到[QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol)结构，该结构保存指向容器使用的指向其自身接口的指针。 类`IQuickActivateImpl`通过在调试生成中向`IQuickActivate`转储设备`IUnknown`发送信息来提供 和 实现的默认实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>I快速激活：：获取内容范围

检索正在运行的控件的当前显示大小。

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>备注

大小用于控件的完整渲染，并在 HIMETRIC 单位中指定。

请参阅[IQuickActivate：在](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent)Windows SDK 中获取内容范围。

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>I 快速激活：：快速激活

对正在加载的控件执行快速初始化。

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>备注

结构包含指向控件所需的接口的指针和某些环境属性的值。 返回后，控件传递指向[QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol)结构的指针，该结构包含指向容器所需的其自身接口的指针和其他状态信息。

请参阅[IQuickActivate：：](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate)在 Windows SDK 中快速激活。

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>I快速激活：：设置内容范围

通知容器为其分配的显示空间的控件。

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>备注

大小以 HIMETRIC 单位指定。

请参阅[IQuickActivate：在](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent)Windows SDK 中设置内容范围。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
