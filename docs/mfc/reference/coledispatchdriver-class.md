---
title: COleDispatchDriver 类
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: fa88147b57b0506f7f9ab96d4a5d2f43fdd75458
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504185"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver 类

实现 OLE 自动化的客户端。

## <a name="syntax"></a>语法

```
class COleDispatchDriver
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|构造 `COleDispatchDriver` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|附加到对象的`IDispatch`连接 `COleDispatchDriver` 。|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|创建连接并将其附加`COleDispatchDriver`到对象。 `IDispatch`|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|`IDispatch`分离连接，而不释放连接。|
|[COleDispatchDriver::GetProperty](#getproperty)|获取自动化属性。|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|用于调用自动化方法的帮助程序。|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|`IDispatch`释放连接。|
|[COleDispatchDriver::SetProperty](#setproperty)|设置自动化属性。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[COleDispatchDriver：： operator =](#operator_eq)|将源值复制到`COleDispatchDriver`对象中。|
|[COleDispatchDriver：： operator LPDISPATCH](#operator_lpdispatch)|访问基础`IDispatch`指针。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|指定`IDispatch`在过程中还是在`ReleaseDispatch`对象析构过程中释放。|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|指示指向附加到此`IDispatch` `COleDispatchDriver`的接口的指针。|

## <a name="remarks"></a>备注

`COleDispatchDriver`没有基类。

OLE 调度接口提供对对象的方法和属性的访问。 `COleDispatchDriver`附加、分离、创建和发布类型`IDispatch`的调度连接的成员函数。 其他成员函数使用变量参数列表简化调用`IDispatch::Invoke`。

此类可以直接使用，但它通常仅由添加类向导创建的类使用。 在通过导入C++类型库创建新类时，新类派生自`COleDispatchDriver`。

有关使用`COleDispatchDriver`的详细信息，请参阅以下文章：

- [自动化客户端](../../mfc/automation-clients.md)

- [自动化服务器](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleDispatchDriver`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="attachdispatch"></a>COleDispatchDriver：： AttachDispatch

调用 `AttachDispatch` 成员函数以将 `IDispatch` 指针附加到 `COleDispatchDriver` 对象。 有关更多信息，请参见 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>参数

*lpDispatch*<br/>
指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。

*bAutoRelease*<br/>
指定当此对象超出范围时是否要释放调度。

### <a name="remarks"></a>备注

此函数会释放任何 `IDispatch` 已附加到 `COleDispatchDriver` 对象的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>COleDispatchDriver：： COleDispatchDriver

构造 `COleDispatchDriver` 对象。

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>参数

*lpDispatch*<br/>
指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。

*bAutoRelease*<br/>
指定当此对象超出范围时是否要释放调度。

*dispatchSrc*<br/>
对现有`COleDispatchDriver`对象的引用。

### <a name="remarks"></a>备注

`COleDispatchDriver`形式（ `LPDISPATCH lpDispatch` 布尔值`bAutoRelease` = TRUE）连接 [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 接口。

窗体`COleDispatchDriver`（ **const**`COleDispatchDriver`&  ）复制`COleDispatchDriver`现有对象并递增引用计数。`dispatchSrc`

窗体`COleDispatchDriver`（）创建对象`COleDispatchDriver` ， `IDispatch`但不连接接口。 在不`COleDispatchDriver`使用参数的情况下使用（）之前`IDispatch` ，应使用[COleDispatchDriver：： CreateDispatch](#createdispatch)或[COleDispatchDriver：： AttachDispatch](#attachdispatch)连接到它。 有关更多信息，请参见 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](#createdispatch)的示例。

##  <a name="createdispatch"></a>COleDispatchDriver：： CreateDispatch

创建一个 [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 接口对象，并将其附加到 `COleDispatchDriver` 对象。

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>参数

*clsid*<br/>
要创建的 `IDispatch` 连接对象的类 ID。

*pError*<br/>
指向 OLE 异常对象的指针，它将保存因创建而产生的状态代码。

*lpszProgID*<br/>
指向要为其创建调度对象的自动化对象的编程标识符的指针，如“Excel.Document.5”。

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>COleDispatchDriver：:D etachDispatch

从此对象分离`IDispatch`当前连接。

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>返回值

指向以前附加的 OLE `IDispatch`对象的指针。

### <a name="remarks"></a>备注

`IDispatch`未释放。

有关 LPDISPATCH 类型的详细信息，请参阅在 Windows SDK 中[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>COleDispatchDriver：： GetProperty

获取*dwDispID*指定的对象属性。

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要检索的属性。

*vtProp*<br/>
指定要检索的属性。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](#invokehelper)。

*pvProp*<br/>
将接收属性值的变量的地址。 它必须与*vtProp*指定的类型匹配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>COleDispatchDriver：： InvokeHelper

在*wFlags*指定的上下文中调用*dwDispID*指定的对象方法或属性。

```
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要调用的方法或属性。

*wFlags*<br/>
描述调用`IDispatch::Invoke`的上下文的标志。 . 有关可能值的列表，请参阅 Windows SDK 中的[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)中的*wFlags*参数。

*vtRet*<br/>
指定返回值的类型。 有关可能值，请参阅“备注”部分。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须与*vtRet*指定的类型匹配。

*pbParamInfo*<br/>
指向以 null 结尾的字节字符串的指针，该字符串指定*pbParamInfo*后面的参数类型。

*...*<br/>
在*pbParamInfo*中指定的类型的参数的变量列表。

### <a name="remarks"></a>备注

*PbParamInfo*参数指定传递到方法或属性的参数的类型。 参数的变量列表在语法声明中通过 **...** 进行表示。

*VtRet*参数的可能值取自 VARENUM 枚举。 可能的值如下：

|符号|返回类型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**变体**|
|VT_UNKNOWN|LPUNKNOWN|

*PbParamInfo*参数是**VTS_** 常量的以空格分隔的列表。 其中一个或多个值（由空格（而不是逗号）分隔）指定函数的参数列表。 可能值使用 [EVENT_CUSTOM](event-maps.md#event_custom) 宏来列出。

此函数将参数转换为 VARIANTARG 值，然后调用[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)方法。 如果 `Invoke` 调用失败，则此函数会引发异常。 如果返回`IDispatch::Invoke`的 SCODE （状态代码）为 DISP_E_EXCEPTION，则此函数将引发[COleException](../../mfc/reference/coleexception-class.md)对象; 否则它将引发[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)。

有关详细信息，请参阅[VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant)、[实现 idispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)、 [IDISPATCH：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)和[COM 错误 Windows SDK 代码的结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](#createdispatch)的示例。

##  <a name="m_bautorelease"></a>COleDispatchDriver：： m_bAutoRelease

如果为 TRUE，则当调用[ReleaseDispatch](#releasedispatch)或此`COleDispatchDriver`对象被销毁时，将自动释放由[m_lpDispatch](#m_lpdispatch)访问的 COM 对象。

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>备注

默认情况下`m_bAutoRelease` ，在构造函数中将设置为 TRUE。

有关释放 COM 对象的详细信息，请参阅 Windows SDK 中的[实现引用计数](/windows/win32/com/implementing-reference-counting)和[IUnknown：： Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>COleDispatchDriver：： m_lpDispatch

指向`IDispatch`附加到此`COleDispatchDriver`的接口的指针。

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>备注

`m_lpDispatch`数据成员是 LPDISPATCH 类型的公共变量。

有关详细信息，请参阅 Windows SDK 中的[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 。

### <a name="example"></a>示例

  请参阅[COleDispatchDriver：： AttachDispatch](#attachdispatch)的示例。

##  <a name="operator_eq"></a>COleDispatchDriver：： operator =

将源值复制到`COleDispatchDriver`对象中。

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>参数

*dispatchSrc*<br/>
指向现有`COleDispatchDriver`对象的指针。

##  <a name="operator_lpdispatch"></a>COleDispatchDriver：： operator LPDISPATCH

访问`COleDispatchDriver`对象的`IDispatch`基础指针。

```
operator LPDISPATCH();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>COleDispatchDriver：： ReleaseDispatch

`IDispatch`释放连接。 有关详细信息，请参阅[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>备注

如果已为此连接设置了自动发布，则此函数`IDispatch::Release`将在释放接口之前调用。

### <a name="example"></a>示例

  请参阅[COleDispatchDriver：： AttachDispatch](#attachdispatch)的示例。

##  <a name="setproperty"></a>COleDispatchDriver：： SetProperty

设置由*dwDispID*指定的 OLE 对象属性。

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的属性。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](#invokehelper)。

*...*<br/>
由*vtProp*指定的类型的单个参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
