---
title: CAxWindow2T 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 077ecfe36e1ddf6c319f02bdabb89d660a5f22d8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 类
此类提供用于操作的窗口，承载 ActiveX 控件，并还具有对承载许可的 ActiveX 控件支持的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```  
  
#### <a name="parameters"></a>参数  
 *TBase*  
 从其类`CAxWindowT`派生。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|构造 `CAxWindow2T` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAxWindow2T::Create](#create)|创建一个主机窗口。|  
|[CAxWindow2T::CreateControlLic](#createcontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|  
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|创建授权的 ActiveX 控件、 对其进行初始化，承载它在指定窗口中，并从控件中检索的接口指针 （或指针）。|  
|[CAxWindow2T::GetWndClassName](#getwndclassname)|检索窗口类的名称的静态方法。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAxWindow2T::operator =](#operator_eq)|将分配`HWND`到一个现有`CAxWindow2T`对象。|  
  
## <a name="remarks"></a>备注  
 `CAxWindow2T` 提供用于操作承载的一个窗口的方法的 ActiveX 控件。 `CAxWindow2T` 此外具有的许可的 ActiveX 控件承载的支持。 提供的托管" **AtlAxWinLic80**"，这由包装`CAxWindow2T`。  
  
 类`CAxWindow2`作为专用化实现`CAxWindow2T`类。 此专用化声明为：  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
> `CAxWindowT` 成员记录下[CAxWindow](../../atl/reference/caxwindow-class.md)。  
  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用此类的成员的示例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
  
##  <a name="caxwindow2t"></a>  CAxWindow2T::CAxWindow2T  
 构造 `CAxWindow2T` 对象。  
  
```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 现有的窗口句柄。  
  
##  <a name="create"></a>  CAxWindow2T::Create  
 创建一个主机窗口。  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="remarks"></a>备注  
 `CAxWindow2T::Create` 调用[CWindow::Create](../../atl/reference/cwindow-class.md#create)与`LPCTSTR lpstrWndClass`参数设置为窗口提供的类的控件承载 ( **AtlAxWinLic80**)。  
  
 请参阅`CWindow::Create`有关参数和返回值的说明。  
  
 **请注意**如果 0 使用的值作为`MenuOrID`参数，必须将它指定为 0U （默认值） 若要避免编译器错误。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`CAxWindow2T::Create`。  
  
##  <a name="createcontrollic"></a>  CAxWindow2T::CreateControlLic  
 创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。  
  
```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bstrLicKey`  
 控件; 许可证密钥如果创建未授权的控件，则为 NULL。  
  
### <a name="remarks"></a>备注  
 请参阅[CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol)有关的剩余的参数和返回值的说明。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`CAxWindow2T::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>  CAxWindow2T::CreateControlLicEx  
 创建授权的 ActiveX 控件、 对其进行初始化，承载它在指定窗口中，并从控件中检索的接口指针 （或指针）。  
  
```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bstrLicKey`  
 控件; 许可证密钥如果创建未授权的控件，则为 NULL。  
  
### <a name="remarks"></a>备注  
 请参阅[CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex)有关的剩余的参数和返回值的说明。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`CAxWindow2T::CreateControlLicEx`。  
  
##  <a name="getwndclassname"></a>  CAxWindow2T::GetWndClassName  
 检索窗口类的名称。  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>返回值  
 指向包含的窗口类名称的字符串的指针 ( **AtlAxWinLic80**)，可以承载授权和未授权的 ActiveX 控件。  
  
##  <a name="operator_eq"></a>  CAxWindow2T::operator =  
 将分配`HWND`到一个现有`CAxWindow2T`对象。  
  
```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 现有的窗口句柄。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [控件包含常见问题](../../atl/atl-control-containment-faq.md)
