---
title: IAxWinHostWindowLic 接口
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: aca3970d13db53ffa04fe9582bbe9b8db78e820d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864848"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 接口

此接口提供用于操作授权控件及其宿主对象的方法。

## <a name="syntax"></a>语法

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Members

### <a name="methods"></a>方法

|||
|-|-|
|[CreateControlLic](#createcontrollic)|创建授权控件，并将其附加到主机对象。|
|[CreateControlLicEx](#createcontrollicex)|创建授权控件，将其附加到主机对象，并选择性地设置事件处理程序。|

## <a name="remarks"></a>备注

`IAxWinHostWindowLic` 继承自[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)并添加支持创建授权控件的方法。

有关使用此接口的成员的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="requirements"></a>要求

此接口的定义以 IDL 或C++的形式提供，如下所示。

|定义类型|文件|
|---------------------|----------|
|.IDL|ATLIFace.idl|
|C++|ATLIFace （也包含在 Atlbase.h 中）|

##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

创建授权控件，对其进行初始化，并将其托管在由 `hWnd`标识的窗口中。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>参数

*bstrLic*<br/>
中包含控件的许可证密钥的 BSTR。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[IAxWinHostWindow：： CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) 。

调用此方法等效于调用[IAxWinHostWindowLic：： CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>示例

有关使用 `IAxWinHostWindowLic::CreateControlLic`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

创建许可的 ActiveX 控件，对其进行初始化，并将其托管在指定窗口中，类似于[IAxWinHostWindow：： CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。

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

*bstrLic*<br/>
中包含控件的许可证密钥的 BSTR。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[IAxWinHostWindow：： CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) 。

### <a name="example"></a>示例

有关使用 `IAxWinHostWindowLic::CreateControlLicEx`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。
