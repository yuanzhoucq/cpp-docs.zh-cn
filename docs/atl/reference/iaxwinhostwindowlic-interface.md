---
title: "IAxWinHostWindowLic 接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61bd50d5602812cc70ccc3201e9df255f469604a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 接口
此接口提供用于操作授权的控件和其主机对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|创建授权的控件并将其附加到该主机对象。|  
|[CreateControlLicEx](#createcontrollicex)|创建授权的控件，将其附加到该主机对象，并根据需要设置事件处理程序。|  
  
## <a name="remarks"></a>备注  
 `IAxWinHostWindowLic`继承自[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)并添加支持授权控件创建的方法。  
  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用此接口的成员的示例。  
  
## <a name="requirements"></a>惠?  
 此接口的定义是 IDL 或 c + +，可用的如下所示。  
  
|定义类型|文件|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包括在 ATLBase.h）|  
  
##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 创建授权的控件，初始化它，并在标识窗口中承载它`hWnd`。  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>参数  
 `bstrLic`  
 [in]BSTR，其中包含该控件的许可证密钥。  
  
### <a name="remarks"></a>备注  
 请参阅[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)有关的剩余的参数和返回值的说明。  
  
 调用此方法等效于调用[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 创建授权的 ActiveX 控件，初始化它，并在指定窗口，类似于中承载它[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。  
  
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
 `bstrLic`  
 [in]BSTR，其中包含该控件的许可证密钥。  
  
### <a name="remarks"></a>备注  
 请参阅[IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)有关的剩余的参数和返回值的说明。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`IAxWinHostWindowLic::CreateControlLicEx`。









