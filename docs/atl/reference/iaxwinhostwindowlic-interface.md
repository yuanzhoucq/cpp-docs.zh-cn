---
title: IAxwinHost窗口接口
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 561a65702f1d4f57b4db1afc75769ce4cc523c1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329913"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxwinHost窗口接口

此接口提供操作许可控件及其主机对象的方法。

## <a name="syntax"></a>语法

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[创建控制](#createcontrollic)|创建许可控件并将其附加到主机对象。|
|[创建控制](#createcontrollicex)|创建许可控件，将其附加到主机对象，并可以选择设置事件处理程序。|

## <a name="remarks"></a>备注

`IAxWinHostWindowLic`从[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)继承，并添加支持创建许可控件的方法。

有关使用此接口的成员的示例，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="requirements"></a>要求

此接口的定义可作为 IDL 或C++，如下所示。

|定义类型|文件|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h （也包含在 ATLBase.h 中）|

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

有关剩余参数和返回值的说明，请参阅[IAxWinHostWindow：创建控制](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。

调用此方法等效于调用[IAxWinHostWindowlic：：创建控制](#createcontrollicex)

### <a name="example"></a>示例

有关 使用`IAxWinHostWindowLic::CreateControlLic`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHost窗口：：创建控制

创建许可的 ActiveX 控件，初始化它，并将其托管在指定的窗口中，类似于[IAxWinHostWindow：：创建控制](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。

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

有关剩余参数和返回值的说明，请参阅[IAxWinHostWindow：创建ControlEx。](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)

### <a name="example"></a>示例

有关 使用`IAxWinHostWindowLic::CreateControlLicEx`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。
