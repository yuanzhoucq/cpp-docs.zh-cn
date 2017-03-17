---
title: "COleDispatchDriver 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- COleDispatchDriver class
- Automation clients, implementing Automation
- OLE dispatch interface
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 51fc2064e2f4b51b4f4328afb03920dab27ef74b
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|将附加`IDispatch`硈`COleDispatchDriver`对象。|  
|[COleDispatchDriver::CreateDispatch](#createdispatch)|创建`IDispatch`连接并将其附加到`COleDispatchDriver`对象。|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|分离`IDispatch`连接，而无需将其释放。|  
|[COleDispatchDriver::GetProperty](#getproperty)|获取的自动化属性。|  
|[COleDispatchDriver::InvokeHelper](#invokehelper)|用于调用自动化的方法的帮助器。|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|版本`IDispatch`连接。|  
|[COleDispatchDriver::SetProperty](#setproperty)|将自动化属性设置。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|将复制源值转换`COleDispatchDriver`对象。|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|访问基础`IDispatch`指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|指定是否释放`IDispatch`期间`ReleaseDispatch`或对象的析构。|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|指示将指针与`IDispatch`接口附加到此`COleDispatchDriver`。|  
  
## <a name="remarks"></a>备注  
 `COleDispatchDriver`没有基类的类。  
  
 OLE 调度接口提供对对象的方法和属性访问。 成员函数`COleDispatchDriver`附加、 分离、 创建和发布类型的调度连接`IDispatch`。 其他成员函数使用变量参数列表来简化调用**idispatch:: Invoke**。  
  
 此类可以直接使用，但它通常仅由添加类向导创建的类。 通过导入类型库中创建新的 c + + 类时，新的类都派生自此`COleDispatchDriver`。  
  
 有关详细信息使用`COleDispatchDriver`，请参阅以下文章︰  
  
- [自动化客户端](../../mfc/automation-clients.md)  
  
- [自动化服务器](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch  
 调用 `AttachDispatch` 成员函数以将 `IDispatch` 指针附加到 `COleDispatchDriver` 对象。 有关详细信息，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpDispatch`  
 指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。  
  
 `bAutoRelease`  
 指定当此对象超出范围时是否要释放调度。  
  
### <a name="remarks"></a>备注  
 此函数会释放任何 `IDispatch` 已附加到 `COleDispatchDriver` 对象的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&3;](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver  
 构造 `COleDispatchDriver` 对象。  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>参数  
 `lpDispatch`  
 指向 OLE `IDispatch` 对象的指针被附加到 `COleDispatchDriver` 对象。  
  
 `bAutoRelease`  
 指定当此对象超出范围时是否要释放调度。  
  
 `dispatchSrc`  
 引用现有`COleDispatchDriver`对象。  
  
### <a name="remarks"></a>备注  
 窗体`COleDispatchDriver`( `LPDISPATCH``lpDispatch`， **BOOL**`bAutoRelease` = **TRUE**) 连接[IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)接口。  
  
 窗体`COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) 将复制的现有`COleDispatchDriver`对象，并递增引用计数。  
  
 窗体`COleDispatchDriver`（） 创建`COleDispatchDriver`对象，但不会连接`IDispatch`接口。 在使用之前`COleDispatchDriver`（不带参数），您应该连接`IDispatch`与其使用[COleDispatchDriver::CreateDispatch](#createdispatch)或[COleDispatchDriver::AttachDispatch](#attachdispatch)。 有关详细信息，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::CreateDispatch](#createdispatch)。  
  
##  <a name="createdispatch"></a>COleDispatchDriver::CreateDispatch  
 创建[IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)接口对象并将其附加到`COleDispatchDriver`对象。  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 要创建的 `IDispatch` 连接对象的类 ID。  
  
 `pError`  
 指向 OLE 异常对象的指针，它将保存因创建而产生的状态代码。  
  
 `lpszProgID`  
 指向要为其创建调度对象的自动化对象的编程标识符的指针，如“Excel.Document.5”。  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&4;](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch  
 分离当前`IDispatch`从该对象的连接。  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>返回值  
 一个指向以前附加 OLE`IDispatch`对象。  
  
### <a name="remarks"></a>备注  
 `IDispatch`不会被释放。  
  
 有关详细信息`LPDISPATCH`类型，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&5;](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>COleDispatchDriver::GetProperty  
 获取由指定的对象属性`dwDispID`。  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwDispID`  
 标识要检索的属性。  
  
 `vtProp`  
 指定要检索的属性。 有关可能的值，请参阅备注部分[COleDispatchDriver::InvokeHelper](#invokehelper)。  
  
 `pvProp`  
 将接收的属性值的变量的地址。 它必须与指定的类型匹配`vtProp`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&6;](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>COleDispatchDriver::InvokeHelper  
 在 `dwDispID`指定的上下文中调用 `wFlags`指定的对象方法或属性。  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>参数  
 `dwDispID`  
 标识要调用的方法或属性。  
  
 `wFlags`  
 描述 **IDispatch::Invoke**调用的上下文的标志。 。 有关可能的值的列表，请参阅`wFlags`中的参数[idispatch:: Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `vtRet`  
 指定返回值的类型。 有关可能值，请参阅“备注”部分。  
  
 `pvRet`  
 将接收属性值或返回值的变量的地址。 它必须与 `vtRet`指定的类型匹配。  
  
 `pbParamInfo`  
 指向以 null 结尾的字符串的指针，该字符串由指定 `pbParamInfo`后面的参数类型的字节组成。  
  
 *...*  
 具有 `pbParamInfo`中指定的类型的参数的变量列表。  
  
### <a name="remarks"></a>备注  
 `pbParamInfo` 参数指定传递到方法或属性的参数的类型。 参数的变量列表在语法声明中通过 **...** 进行表示。  
  
 `vtRet` 参数的可能值取自 `VARENUM` 枚举。 可能的值如下：  
  
|符号|返回类型|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**双精度**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT 类型的值**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `pbParamInfo` 参数是 **VTS_** 常量的以空格分隔的列表。 其中一个或多个值（由空格（而不是逗号）分隔）指定函数的参数列表。 列出了可能的值[EVENT_CUSTOM](event-maps.md#event_custom)宏。  
  
 此函数将参数转换为 **VARIANTARG** 值，然后调用 [IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) 方法。 如果 `Invoke` 调用失败，则此函数会引发异常。 如果`SCODE`（状态代码） 返回**idispatch:: Invoke**是`DISP_E_EXCEPTION`，此函数将引发[COleException](../../mfc/reference/coleexception-class.md)对象; 否则它将引发[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)。  
  
 有关详细信息，请参阅[VARIANTARG](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)，[实现 IDispatch 接口](http://msdn.microsoft.com/library/windows/desktop/ms221037\(v=vs.85\).aspx)， [idispatch:: Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx)，和[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::CreateDispatch](#createdispatch)。  
  
##  <a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease  
 如果**TRUE**，访问的 COM 对象[m_lpDispatch](#m_lpdispatch)将时自动释放[ReleaseDispatch](#releasedispatch)调用时，或者当这`COleDispatchDriver`对象被销毁。  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，`m_bAutoRelease`设置为**TRUE**构造函数中。  
  
 释放 COM 对象的详细信息，请参阅[实现引用计数](http://msdn.microsoft.com/library/windows/desktop/ms693431)和[iunknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&9;](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch  
 将指针与`IDispatch`接口附加到此`COleDispatchDriver`。  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>备注  
 `m_lpDispatch`数据成员是类型的公共变量`LPDISPATCH`。  
  
 有关详细信息，请参阅[IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::AttachDispatch](#attachdispatch)。  
  
##  <a name="operator_eq"></a>COleDispatchDriver::operator =  
 将复制源值转换`COleDispatchDriver`对象。  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>参数  
 `dispatchSrc`  
 一个指向现有`COleDispatchDriver`对象。  
  
##  <a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH  
 访问基础`IDispatch`指针`COleDispatchDriver`对象。  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&8;](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch  
 版本`IDispatch`连接。 有关详细信息，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>备注  
 如果已为此连接设置自动释放，此函数将调用**IDispatch::Release**之前释放接口。  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::AttachDispatch](#attachdispatch)。  
  
##  <a name="setproperty"></a>COleDispatchDriver::SetProperty  
 设置由 `dwDispID`指定的 OLE 对象属性。  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>参数  
 `dwDispID`  
 标识要设置的属性。  
  
 `vtProp`  
 指定要设置的属性的类型。 有关可能的值，请参阅备注部分[COleDispatchDriver::InvokeHelper](#invokehelper)。  
  
 *...*  
 由 `vtProp`指定的类型的单个参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&7;](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CALCDRIV](../../visual-cpp-samples.md)   
 [MFC 示例 ACDUAL](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)

