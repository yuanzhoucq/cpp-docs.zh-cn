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
ms.openlocfilehash: 2b52ed3137a9a515278e018d69751aedaddb0cf1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753891"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver 类

实现 OLE 自动化的客户端。

## <a name="syntax"></a>语法

```
class COleDispatchDriver
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle调度驱动程序：COle调度驱动程序](#coledispatchdriver)|构造 `COleDispatchDriver` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle调度驱动程序：：附加调度](#attachdispatch)|将`IDispatch`连接附加到`COleDispatchDriver`对象。|
|[COle调度驱动程序：创建调度](#createdispatch)|创建`IDispatch`连接并将其附加到`COleDispatchDriver`对象。|
|[COle调度驱动程序：:Detach调度](#detachdispatch)|分离`IDispatch`连接，而不释放它。|
|[COle调度驱动程序：获取财产](#getproperty)|获取自动化属性。|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|用于调用自动化方法的帮助器。|
|[COle调度驱动程序：：发布调度](#releasedispatch)|释放`IDispatch`连接。|
|[COle调度驱动程序：：设置属性](#setproperty)|设置自动化属性。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[COle调度驱动程序：：操作员 |](#operator_eq)|将源值复制到对象中`COleDispatchDriver`。|
|[COle调度驱动程序：：操作员 LPDISPATCH](#operator_lpdispatch)|访问基础`IDispatch`指针。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COle调度驱动程序：m_bAutoRelease](#m_bautorelease)|指定是释放`IDispatch`销毁期间`ReleaseDispatch`还是对象销毁。|
|[COle调度驱动程序：m_lpDispatch](#m_lpdispatch)|指示指向附加到此`IDispatch``COleDispatchDriver`的接口的指针。|

## <a name="remarks"></a>备注

`COleDispatchDriver`没有基类。

OLE 调度接口提供对对象方法和属性的访问。 `COleDispatchDriver`附加、分离、创建和释放类型的`IDispatch`调度连接的成员函数。 其他成员函数使用变量参数列表来简化调用`IDispatch::Invoke`。

此类可以直接使用，但通常仅由添加类向导创建的类使用。 通过导入类型库创建新C++类时，新类派生自`COleDispatchDriver`。

有关 使用`COleDispatchDriver`的详细信息，请参阅以下文章：

- [自动化客户端](../../mfc/automation-clients.md)

- [自动化服务器](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleDispatchDriver`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COle调度驱动程序：：附加调度

调用 `AttachDispatch` 成员函数以将 `IDispatch` 指针附加到 `COleDispatchDriver` 对象。 有关详细信息，请参阅 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

```cpp
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>参数

*lpDispatch*<br/>
指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。

*b自动释放*<br/>
指定当此对象超出范围时是否要释放调度。

### <a name="remarks"></a>备注

此函数会释放任何 `IDispatch` 已附加到 `COleDispatchDriver` 对象的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COle调度驱动程序：COle调度驱动程序

构造 `COleDispatchDriver` 对象。

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>参数

*lpDispatch*<br/>
指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。

*b自动释放*<br/>
指定当此对象超出范围时是否要释放调度。

*调度Src*<br/>
对现有`COleDispatchDriver`对象的引用。

### <a name="remarks"></a>备注

窗体`COleDispatchDriver`（ `LPDISPATCH lpDispatch`， **BOOL**`bAutoRelease` = **TRUE**） 连接[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)接口。

`COleDispatchDriver`窗体 （ **const**`COleDispatchDriver`& `dispatchSrc`）`COleDispatchDriver`复制现有对象并递增引用计数。

窗体`COleDispatchDriver`（ ）`COleDispatchDriver`创建一个对象，`IDispatch`但不连接接口。 在不使用`COleDispatchDriver`（ ） 之前，应`IDispatch`使用[COleDispatchDriver：：创建调度](#createdispatch)或[COleDispatch驱动程序：：附加调度](#attachdispatch)。 有关详细信息，请参阅 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](#createdispatch)的示例。

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COle调度驱动程序：创建调度

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

*Clsid*<br/>
要创建的 `IDispatch` 连接对象的类 ID。

*pError*<br/>
指向 OLE 异常对象的指针，它将保存因创建而产生的状态代码。

*lpszProgID*<br/>
指向要为其创建调度对象的自动化对象的编程标识符的指针，如“Excel.Document.5”。

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COle调度驱动程序：:Detach调度

从此对象分离`IDispatch`当前连接。

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>返回值

指向以前附加的 OLE`IDispatch`对象的指针。

### <a name="remarks"></a>备注

`IDispatch`未释放。

有关 LPDISPATCH 类型的详细信息，请参阅在 Windows SDK 中[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COle调度驱动程序：获取财产

获取*dwDispID*指定的对象属性。

```cpp
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
将接收属性值的变量的地址。 它必须匹配*vtProp*指定的类型。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COle调度驱动程序：：调用帮助器

在*wFlags*指定的上下文中调用*dwDispID*指定的对象方法或属性。

```cpp
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
描述对`IDispatch::Invoke`的调用上下文的标志。 . 有关可能值的列表，请参阅[IDispatch：：：在](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)Windows SDK 中的调用中的*wFlags*参数。

*弗特雷特*<br/>
指定返回值的类型。 有关可能值，请参阅“备注”部分。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须与*vtRet*指定的类型匹配。

*pbParamInfo*<br/>
指向 null 端接字节字符串的指针，指定*pbParamInfo*之后的参数类型。

*...*<br/>
参数的变量列表，在*pbParamInfo*中指定的类型。

### <a name="remarks"></a>备注

*pbParamInfo*参数指定传递给方法或属性的参数的类型。 参数的变量列表在语法声明中通过 **...** 进行表示。

*vtRet*参数的可能值取自 VARENUM 枚举。 可能的值如下所示：

|符号|返回类型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**日期**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**Bool**|
|VT_VARIANT|**变异**|
|VT_UNKNOWN|LPUNKNOWN|

*pbParamInfo*参数是**VTS_** 常量的空间分隔列表。 其中一个或多个值（由空格（而不是逗号）分隔）指定函数的参数列表。 可能值使用 [EVENT_CUSTOM](event-maps.md#event_custom) 宏来列出。

此函数将参数转换为 VARIANTARG 值，然后调用 [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 方法。 如果 `Invoke` 调用失败，则此函数会引发异常。 如果返回的 SCODE（状态代码）DISP_E_EXCEPTION，则此函数将引发一个 COleException 对象;如果返回`IDispatch::Invoke`的 SCODE（状态代码）DISP_E_EXCEPTION，则此函数将引发一个[COleException](../../mfc/reference/coleexception-class.md)对象。否则，它抛出一个[COleDispatch例外](../../mfc/reference/coledispatchexception-class.md)。

有关详细信息，请参阅[VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant)，[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) [、IDispatch：：：调用](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)和 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](#createdispatch)的示例。

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COle调度驱动程序：m_bAutoRelease

如果为 TRUE，则[当](#m_lpdispatch)调用[ReleaseDispatch](#releasedispatch)或销毁此`COleDispatchDriver`对象时，m_lpDispatch访问的 COM 对象将自动释放。

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>备注

默认情况下，`m_bAutoRelease`在构造函数中设置为 TRUE。

有关释放 COM 对象的详细信息，请参阅在 Windows SDK 中[实现引用计数](/windows/win32/com/implementing-reference-counting)和[I 未知：：发布](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COle调度驱动程序：m_lpDispatch

指向附加到此`COleDispatchDriver`的`IDispatch`接口的指针。

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>备注

数据`m_lpDispatch`成员是 LPDISPATCH 类型的公共变量。

有关详细信息，请参阅 Windows SDK 中的[IDispatch。](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

### <a name="example"></a>示例

  请参阅[COleDispatch 驱动程序的示例：：附加调度](#attachdispatch)。

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COle调度驱动程序：：操作员 |

将源值复制到对象中`COleDispatchDriver`。

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>参数

*调度Src*<br/>
指向现有`COleDispatchDriver`对象的指针。

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COle调度驱动程序：：操作员 LPDISPATCH

访问`IDispatch``COleDispatchDriver`对象的基础指针。

```
operator LPDISPATCH();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COle调度驱动程序：：发布调度

释放`IDispatch`连接。 有关详细信息，请参阅实现[IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>备注

如果已为此连接设置了自动释放，则此函数在释放`IDispatch::Release`接口之前调用。

### <a name="example"></a>示例

  请参阅[COleDispatch 驱动程序的示例：：附加调度](#attachdispatch)。

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COle调度驱动程序：：设置属性

设置*dwDispID*指定的 OLE 对象属性。

```cpp
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
*vtProp*指定的类型的单个参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
