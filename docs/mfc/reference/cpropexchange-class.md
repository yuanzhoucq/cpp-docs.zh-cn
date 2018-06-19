---
title: CPropExchange 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
dev_langs:
- C++
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f234b3f06e22308a31e8e5694648fd5664b448a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377335"
---
# <a name="cpropexchange-class"></a>CPropExchange 类
支持 OLE 控件持久性的实现。  
  
## <a name="syntax"></a>语法  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|交换的二进制大型对象 (BLOB) 属性。|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|交换的字体属性。|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|交换控件和文件之间的属性。|  
|[CPropExchange::ExchangeProp](#exchangeprop)|交换任何内置类型的属性。|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|交换 OLE 控件的版本号。|  
|[CPropExchange::GetVersion](#getversion)|检索 OLE 控件的版本号。|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|确定属性交换以异步方式完成。|  
|[CPropExchange::IsLoading](#isloading)|指示是否属性正在加载到控件，或从其保存。|  
  
## <a name="remarks"></a>备注  
 `CPropExchange` 没有基类。  
  
 建立的上下文和属性交换的方向。  
  
 持久性是控件的状态信息，通常由其属性，该控件本身和中等之间的交换。  
  
 框架将构造一个对象派生自`CPropExchange`当通知 OLE 控件的属性是从加载或存储到持久存储。  
  
 框架将指针传递到这`CPropExchange`到控件的对象`DoPropExchange`函数。 如果您使用向导为您的控件，您的控件的创建的初学者文件`DoPropExchange`函数调用`COleControl::DoPropExchange`。 基类版本交换控件的常用属性;修改派生的类的版本到 exchange 属性已添加到你的控件。  
  
 `CPropExchange` 可以用于序列化控件的属性或初始化在加载或创建控件时控件的属性。 `ExchangeProp`和`ExchangeFontProp`的成员函数`CPropExchange`能够存储到的属性并将它们加载从不同的媒体。  
  
 有关详细信息使用`CPropExchange`，请参阅文章[MFC ActiveX 控件： 属性页](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CPropExchange`  
  
## <a name="requirements"></a>要求  
 **标头：** afxctl.h  
  
##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp  
 序列化存储二进制大型对象 (BLOB) 数据的属性。  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pszPropName`  
 要交换的属性的名称。  
  
 `phBlob`  
 指针到指向该属性的存储位置的变量 （变量通常是你的类的成员）。  
  
 `hBlobDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入，根据需要，引用的变量属性的值`phBlob`。 如果`hBlobDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控制的序列化失败，则使用此值。  
  
 函数**CArchivePropExchange::ExchangeBlobProp**， **CResetPropExchange::ExchangeBlobProp**，和**CPropsetPropExchange::ExchangeBlobProp**重写此纯虚拟函数。  
  
##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp  
 交换存储媒介与控件之间的字体属性。  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pszPropName`  
 要交换的属性的名称。  
  
 `font`  
 对引用[CFontHolder](../../mfc/reference/cfontholder-class.md)包含字体属性的对象。  
  
 `pFontDesc`  
 指向的指针[FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)结构，它包含用于初始化字体属性的默认状态的值时`pFontDispAmbient`是**NULL**。  
  
 `pFontDispAmbient`  
 指向的指针**IFontDisp**接口的一种字体用于初始化字体属性的默认状态。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 如果字体属性从介质加载到控件时，将从该媒体检索字体的特征和`CFontHolder`所引用对象`font`与其初始化。 如果正在存储字体属性，字体对象中的特征写入到介质。  
  
 函数**CArchivePropExchange::ExchangeFontProp**， **CResetPropExchange::ExchangeFontProp**，和**CPropsetPropExchange::ExchangeFontProp**重写此纯虚拟函数。  
  
##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp  
 交换控件文件之间的属性。  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pszPropName`  
 要交换的属性的名称。  
  
 `ppUnk`  
 指向包含的属性指向的指针的变量的指针**IUnknown** （此变量通常是你的类的成员） 的接口。  
  
 `iid`  
 在控件将使用的属性上的接口的接口 ID。  
  
 `pUnkDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 如果属性正在从文件加载到控件，该属性是创建并初始化从文件。 如果正在存储属性，其值写入文件。  
  
 函数**CArchivePropExchange::ExchangePersistentProp**， **CResetPropExchange::ExchangePersistentProp**，和**CPropsetPropExchange::ExchangePersistentProp**重写此纯虚函数。  
  
##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp  
 交换存储媒介与控件之间的属性。  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>参数  
 `pszPropName`  
 要交换的属性的名称。  
  
 `vtProp`  
 指定要交换的属性的类型的符号。 可能的值有：  
  
|符号|属性类型|  
|------------|-------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_BOOL`|**BOOL**|  
|`VT_BSTR`|`CString`|  
|`VT_CY`|**CY**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
  
 `pvProp`  
 指向该属性的值的指针。  
  
 *pvDefault*  
 转换为属性的默认值的指针。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 从媒体中检索属性从介质加载到控件时，如果属性的值并存储指向的对象在`pvProp`。 如果属性存储到介质，对象的值的指向`pvProp`写入介质。  
  
 函数**CArchivePropExchange::ExchangeProp**， **CResetPropExchange::ExchangeProp**，和**CPropsetPropExchange::ExchangeProp**替代这纯虚函数。  
  
##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion  
 由框架调用以处理持久性的版本号。  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>参数  
 *dwVersionLoaded*  
 对将存储永久性数据正在加载的版本号的变量的引用。  
  
 `dwVersionDefault`  
 控件的当前版本号。  
  
 `bConvert`  
 指示是否将持久数据转换为最新版本，或使其保持已加载的版本相同。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
##  <a name="getversion"></a>  CPropExchange::GetVersion  
 调用此函数可检索的控件的版本号。  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>返回值  
 控件的版本号。  
  
##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous  
 确定属性交换以异步方式完成。  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>返回值  
 返回 TRUE，如果属性是以异步方式交换; 否则为 FALSE。  
  
##  <a name="isloading"></a>  CPropExchange::IsLoading  
 调用此函数可确定是否正在属性加载到控件或从其保存。  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>返回值  
 正在加载属性; 如果非零否则为 0。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)



