---
title: "IAxWinHostWindowLic 界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 01ff8a7205418583606cbfdb1c028d7097501e00
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 接口
此接口提供用于操作授权的控件和其宿主对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|创建一个授权的控件，并将其附加到该主机对象。|  
|[CreateControlLicEx](#createcontrollicex)|创建一个授权的控件，将其附加到该主机对象，并根据需要设置一个事件处理程序。|  
  
## <a name="remarks"></a>备注  
 `IAxWinHostWindowLic`继承自[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)并添加支持的授权控件创建的方法。  
  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关的示例，使用此接口的成员。  
  
## <a name="requirements"></a>要求  
 此接口的定义可用作 IDL 或 c + +，如下所示。  
  
|定义类型|文件|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包括在 ATLBase.h）|  
  
##  <a name="a-namecreatecontrollica--iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
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
 [in]包含控件的许可证密钥 BSTR。  
  
### <a name="remarks"></a>备注  
 请参阅[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)有关其余参数和返回值的说明。  
  
 调用此方法等效于调用[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关的示例，使用`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="a-namecreatecontrollicexa--iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 创建授权的 ActiveX 控件，初始化它并将它宿主在指定窗口中，类似于[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。  
  
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
 [in]包含控件的许可证密钥 BSTR。  
  
### <a name="remarks"></a>备注  
 请参阅[IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)有关其余参数和返回值的说明。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关的示例，使用`IAxWinHostWindowLic::CreateControlLicEx`。










