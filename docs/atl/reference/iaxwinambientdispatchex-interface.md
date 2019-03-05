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
ms.openlocfilehash: ae91921ecd5f53f4551e46e1d03cf027ce3e1f3b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292392"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 接口

此接口实现托管控件的补充环境的属性。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|调用此方法来补充使用用户定义的接口的默认环境属性接口。|

## <a name="remarks"></a>备注

在静态链接到 ATL 和主机的 ActiveX 控件，尤其是具有环境属性的 ActiveX 控件的 ATL 应用程序中包含此接口。 不包括此接口将生成此断言："您忘记了要传递给 CComModule::Init 的 LIBID"

此接口由 ATL 的 ActiveX 控件承载对象公开。 派生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`添加允许你补充由 ATL 提供与您自己的环境属性接口的方法。

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)会尝试加载有关类型信息`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从类型库包含的代码。

如果要链接到 ATL90.dll， **AXHost**将加载 DLL 中的类型库中的类型信息。

请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的更多详细信息。

## <a name="requirements"></a>要求

此接口的定义有多种形式下, 表中所示。

|定义类型|文件|
|---------------------|----------|
|IDL|atliface.idl|
|类型库|ATL.dll|
|C++|atliface.h （也包括在 ATLBase.h）|

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

调用此方法来补充使用用户定义的接口的默认环境属性接口。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>参数

*pDispatch*<br/>
指向新接口指针。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

当`SetAmbientDispatch`调用与对新接口指针，此新接口将用于调用的任何属性或方法请求的托管控件，如果这些属性不会由已提供[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>请参阅

[IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)
