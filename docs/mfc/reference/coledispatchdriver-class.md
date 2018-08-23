---
title: COleDispatchDriver 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61e4a36db71809dab5603211dce91fad3eedd082
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "42540993"
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
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|将附加`IDispatch`连接到`COleDispatchDriver`对象。|  
|[Coledispatchdriver:: Createdispatch](#createdispatch)|创建`IDispatch`连接并将其附加到`COleDispatchDriver`对象。|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|分离`IDispatch`连接，而不释放它。|  
|[COleDispatchDriver::GetProperty](#getproperty)|获取自动化属性。|  
|[Coledispatchdriver:: Invokehelper](#invokehelper)|调用自动化方法的帮助器。|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|版本`IDispatch`连接。|  
|[COleDispatchDriver::SetProperty](#setproperty)|设置自动化属性。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|将复制到源值`COleDispatchDriver`对象。|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|访问基础`IDispatch`指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|指定是否释放`IDispatch`期间`ReleaseDispatch`或对象析构。|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|指示指针，指向`IDispatch`接口附加到此`COleDispatchDriver`。|  
  
## <a name="remarks"></a>备注  
 `COleDispatchDriver` 没有基类。  
  
 OLE 调度接口提供对对象的方法和属性访问。 成员函数`COleDispatchDriver`附加、 分离、 创建和发布类型的调度连接`IDispatch`。 其他成员函数使用变量自变量列表来简化调用`IDispatch::Invoke`。  
  
 此类可以直接使用，但它通常仅由添加类向导创建的类。 通过导入类型库中创建新的 c + + 类时，将新的类派生自`COleDispatchDriver`。  
  
 有关详细信息使用`COleDispatchDriver`，请参阅以下文章：  
  
- [自动化客户端](../../mfc/automation-clients.md)  
  
- [自动化服务器](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="attachdispatch"></a>  COleDispatchDriver::AttachDispatch  
 调用 `AttachDispatch` 成员函数以将 `IDispatch` 指针附加到 `COleDispatchDriver` 对象。 有关详细信息，请参阅[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *lpDispatch*  
 指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。  
  
 *bAutoRelease*  
 指定当此对象超出范围时是否要释放调度。  
  
### <a name="remarks"></a>备注  
 此函数会释放任何 `IDispatch` 已附加到 `COleDispatchDriver` 对象的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>  COleDispatchDriver::COleDispatchDriver  
 构造 `COleDispatchDriver` 对象。  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>参数  
 *lpDispatch*  
 指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。  
  
 *bAutoRelease*  
 指定当此对象超出范围时是否要释放调度。  
  
 *dispatchSrc*  
 引用添加到现有`COleDispatchDriver`对象。  
  
### <a name="remarks"></a>备注  
 在窗体`COleDispatchDriver`( `LPDISPATCH lpDispatch`， **BOOL**`bAutoRelease` = **TRUE**) 连接[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)接口。  
  
 在窗体`COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) 将复制的现有`COleDispatchDriver`对象并递增引用计数。  
  
 在窗体`COleDispatchDriver`（） 创建`COleDispatchDriver`对象，但不会连接`IDispatch`接口。 使用之前`COleDispatchDriver`（不带参数），则应在连接`IDispatch`与其使用[coledispatchdriver:: Createdispatch](#createdispatch)或[COleDispatchDriver::AttachDispatch](#attachdispatch)。 有关详细信息，请参阅[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[coledispatchdriver:: Createdispatch](#createdispatch)。  
  
##  <a name="createdispatch"></a>  Coledispatchdriver:: Createdispatch  
 创建[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)接口对象并将其附加到`COleDispatchDriver`对象。  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 *clsid*  
 要创建的 `IDispatch` 连接对象的类 ID。  
  
 *pError*  
 指向 OLE 异常对象的指针，它将保存因创建而产生的状态代码。  
  
 *lpszProgID*  
 指向要为其创建调度对象的自动化对象的编程标识符的指针，如“Excel.Document.5”。  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>  COleDispatchDriver::DetachDispatch  
 分离当前`IDispatch`此对象的连接。  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>返回值  
 指向以前附加 OLE`IDispatch`对象。  
  
### <a name="remarks"></a>备注  
 `IDispatch`不会被释放。  
  
 有关 LPDISPATCH 类型的详细信息，请参阅[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>  COleDispatchDriver::GetProperty  
 获取指定的对象属性*dwDispID*。  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>参数  
 *dwDispID*  
 标识要检索的属性。  
  
 *vtProp*  
 指定要检索的属性。 有关可能的值，请参阅备注部分[coledispatchdriver:: Invokehelper](#invokehelper)。  
  
 *pvProp*  
 将接收属性值的变量的地址。 它必须匹配指定的类型*vtProp*。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>  Coledispatchdriver:: Invokehelper  
 调用对象方法或属性指定的*dwDispID*，在指定的上下文*wFlags*。  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>参数  
 *dwDispID*  
 标识要调用的方法或属性。  
  
 *wFlags*  
 描述对调用上下文的标志`IDispatch::Invoke`。 . 有关可能的值的列表，请参阅*wFlags*中的参数[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) Windows SDK 中。  
  
 *vtRet*  
 指定返回值的类型。 有关可能值，请参阅“备注”部分。  
  
 *pvRet*  
 将接收属性值或返回值的变量的地址。 它必须匹配指定的类型*vtRet*。  
  
 *pbParamInfo*  
 指向以 null 结尾字节指定后面的参数的类型的字符串指针*pbParamInfo*。  
  
 *...*  
 参数中指定的类型的变量列表*pbParamInfo*。  
  
### <a name="remarks"></a>备注  
 *PbParamInfo*参数指定的参数传递到方法或属性的类型。 参数的变量列表在语法声明中通过 **...** 进行表示。  
  
 可能的值*vtRet* VARENUM 枚举中采用参数。 可能的值如下：  
  
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
  
 *PbParamInfo*参数是以空格分隔的列表**VTS_** 常量。 其中一个或多个值（由空格（而不是逗号）分隔）指定函数的参数列表。 列出可能的值[EVENT_CUSTOM](event-maps.md#event_custom)宏。  
  
 此函数将参数转换为 VARIANTARG 值，然后调用[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)方法。 如果 `Invoke` 调用失败，则此函数会引发异常。 如果返回 SCODE （状态代码），那么`IDispatch::Invoke`是 DISP_E_EXCEPTION，此函数将引发[COleException](../../mfc/reference/coleexception-class.md)对象; 否则将引发[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)。  
  
 有关详细信息，请参阅[VARIANTARG](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)，[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)， [idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)，和[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088) Windows SDK 中。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[coledispatchdriver:: Createdispatch](#createdispatch)。  
  
##  <a name="m_bautorelease"></a>  COleDispatchDriver::m_bAutoRelease  
 如果为 TRUE，COM 对象的访问[m_lpDispatch](#m_lpdispatch)将时自动释放[ReleaseDispatch](#releasedispatch)调用时，或者当这`COleDispatchDriver`对象被销毁。  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，`m_bAutoRelease`构造函数中设置为 TRUE。  
  
 释放 COM 对象的详细信息，请参阅[实现引用计数](http://msdn.microsoft.com/library/windows/desktop/ms693431)并[iunknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>  COleDispatchDriver::m_lpDispatch  
 指向指针`IDispatch`接口附加到此`COleDispatchDriver`。  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>备注  
 `m_lpDispatch`数据成员是类型 LPDISPATCH 的公共变量。  
  
 有关详细信息，请参阅[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) Windows SDK 中。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[COleDispatchDriver::AttachDispatch](#attachdispatch)。  
  
##  <a name="operator_eq"></a>  COleDispatchDriver::operator =  
 将复制到源值`COleDispatchDriver`对象。  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>参数  
 *dispatchSrc*  
 一个指向现有`COleDispatchDriver`对象。  
  
##  <a name="operator_lpdispatch"></a>  COleDispatchDriver::operator LPDISPATCH  
 访问基础`IDispatch`指针的`COleDispatchDriver`对象。  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>  COleDispatchDriver::ReleaseDispatch  
 版本`IDispatch`连接。 有关详细信息，请参阅[实现 IDispatch 接口](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>备注  
 如果已为此连接设置自动发布，此函数将调用`IDispatch::Release`之前释放接口。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[COleDispatchDriver::AttachDispatch](#attachdispatch)。  
  
##  <a name="setproperty"></a>  COleDispatchDriver::SetProperty  
 设置指定的 OLE 对象属性*dwDispID*。  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>参数  
 *dwDispID*  
 标识要设置的属性。  
  
 *vtProp*  
 指定要设置的属性的类型。 有关可能的值，请参阅备注部分[coledispatchdriver:: Invokehelper](#invokehelper)。  
  
 *...*  
 指定的类型的单个参数*vtProp*。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CALCDRIV](../../visual-cpp-samples.md)   
 [MFC 示例 ACDUAL](../../visual-cpp-samples.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
