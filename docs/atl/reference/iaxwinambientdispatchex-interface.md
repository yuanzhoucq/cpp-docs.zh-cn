---
title: IAxWinAmbientDispatchEx 接口
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329982"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 接口

此接口为托管控件实现补充环境属性。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[设置环境调度](#setambientdispatch)|调用此方法是为了使用用户定义的接口补充默认环境属性接口。|

## <a name="remarks"></a>备注

此接口包含在以静态链接到 ATL 和主机 ActiveX 控件的 ATL 应用程序中，尤其是具有环境属性的 ActiveX 控件。 不包括此接口将生成此断言："您是否忘记将 LIBID 传递给 CComModule：：Init"

此接口由 ATL 的 ActiveX 控件托管对象公开。 派生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`添加了一种方法，允许您用您自己的一种来补充 ATL 提供的环境属性接口。

<xref:System.Windows.Forms.AxHost>将尝试加载有关`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从包含代码的类型库的类型信息。

如果要链接到 ATL90.dll，AXHost 将从 DLL 中的类型库中加载类型信息。 **AXHost**

有关详细信息[，请参阅使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="requirements"></a>要求

此接口的定义有多种形式可用，如下表所示。

|定义类型|文件|
|---------------------|----------|
|Idl|atliface.idl|
|类型库|ATL.dll|
|C++|atliface.h （也包含在 ATLBase.h 中）|

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

当`SetAmbientDispatch`使用指向新接口的指针调用时，如果[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)尚未提供这些属性，则此新接口将用于调用托管控件要求的任何属性或方法。

## <a name="see-also"></a>另请参阅

[IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)
