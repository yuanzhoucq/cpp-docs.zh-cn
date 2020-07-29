---
title: CPropExchange 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 09fb1bd34f3b5eadb78d8f9081450c042fe22f9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226862"
---
# <a name="cpropexchange-class"></a>CPropExchange 类

支持 OLE 控件持久性的实现。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|交换二进制大型对象（BLOB）属性。|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|交换字体属性。|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|交换控件和文件之间的属性。|
|[CPropExchange::ExchangeProp](#exchangeprop)|交换任何内置类型的属性。|
|[CPropExchange::ExchangeVersion](#exchangeversion)|交换 OLE 控件的版本号。|
|[CPropExchange：： GetVersion](#getversion)|检索 OLE 控件的版本号。|
|[CPropExchange：： IsAsynchronous](#isasynchronous)|确定是否异步完成属性交换。|
|[CPropExchange：： IsLoading](#isloading)|指示属性是加载到控件中还是从其保存。|

## <a name="remarks"></a>备注

`CPropExchange`没有基类。

建立属性交换的上下文和方向。

持久性是控件的状态信息的交换，通常由其属性在控件本身和介质之间表示。

`CPropExchange`当通知要从持久性存储区加载 OLE 控件的属性或将其存储到永久性存储时，框架将构造从派生的对象。

框架将此对象的指针传递 `CPropExchange` 到控件的 `DoPropExchange` 函数。 如果使用向导创建控件的起始文件，则控件的 `DoPropExchange` 函数会调用 `COleControl::DoPropExchange` 。 基类版本交换控件的常用属性;将派生类的版本修改为已添加到控件的 exchange 属性。

`CPropExchange`可用于在控件的加载或创建时序列化控件的属性或初始化控件的属性。 的 `ExchangeProp` 和 `ExchangeFontProp` 成员函数 `CPropExchange` 可以将属性存储到不同的媒体并从中加载它们。

有关使用的详细信息 `CPropExchange` ，请参阅[MFC ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CPropExchange`

## <a name="requirements"></a>要求

**标头：** afxctl。h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

序列化存储二进制大型对象（BLOB）数据的属性。

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>参数

*pszPropName*<br/>
要交换的属性的名称。

*phBlob*<br/>
指向一个变量的指针，该变量指向属性的存储位置（变量通常是类的成员）。

*hBlobDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

此属性的值将在适当的情况下读取或写入*phBlob*引用的变量。 如果指定了*hBlobDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化失败，则使用此值。

函数 `CArchivePropExchange::ExchangeBlobProp` 、 `CResetPropExchange::ExchangeBlobProp` 和将 `CPropsetPropExchange::ExchangeBlobProp` 重写此纯虚函数。

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

在存储介质和控件之间交换字体属性。

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>参数

*pszPropName*<br/>
要交换的属性的名称。

*文字*<br/>
对包含 font 属性的[CFontHolder](../../mfc/reference/cfontholder-class.md)对象的引用。

*pFontDesc*<br/>
指向[FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)结构的指针，该结构包含用于在*pFontDispAmbient*为 NULL 时初始化 font 属性的默认状态的值。

*pFontDispAmbient*<br/>
指向 `IFontDisp` 用于初始化 font 属性的默认状态的字体接口的指针。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

如果将 font 属性从介质加载到控件，则会从介质中检索字体的特征，并 `CFontHolder` 使用它们对*字体*所引用的对象进行初始化。 如果正在存储字体属性，则会将 font 对象中的特征写入介质。

函数 `CArchivePropExchange::ExchangeFontProp` 、 `CResetPropExchange::ExchangeFontProp` 和将 `CPropsetPropExchange::ExchangeFontProp` 重写此纯虚函数。

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

交换控件和文件之间的属性。

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>参数

*pszPropName*<br/>
要交换的属性的名称。

*ppUnk*<br/>
指向一个变量的指针，该变量包含指向属性接口的指针 `IUnknown` （此变量通常为类的成员）。

*iid*<br/>
控件将使用的属性的接口 ID。

*pUnkDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

如果该属性是从文件加载到控件的，则将从该文件创建并初始化属性。 如果属性正在存储，则将其值写入文件。

函数 `CArchivePropExchange::ExchangePersistentProp` 、 `CResetPropExchange::ExchangePersistentProp` 和将 `CPropsetPropExchange::ExchangePersistentProp` 重写此纯虚函数。

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

在存储介质和控件之间交换属性。

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>参数

*pszPropName*<br/>
要交换的属性的名称。

*vtProp*<br/>
指定正在交换的属性的类型的符号。 可能的值包括：

|符号|属性类型|
|------------|-------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_BOOL|**型**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|

*pvProp*<br/>
指向属性值的指针。

*pvDefault*<br/>
指向属性的默认值的指针。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

如果该属性是从介质加载到控件的，则将从中检索该属性的值，并将其存储在*pvProp*所指向的对象中。 如果将属性存储在介质上，则*pvProp*指向的对象的值将写入介质。

函数 `CArchivePropExchange::ExchangeProp` 、 `CResetPropExchange::ExchangeProp` 和将 `CPropsetPropExchange::ExchangeProp` 重写此纯虚函数。

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

由框架调用，用于处理版本号的持久性。

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>参数

*dwVersionLoaded*<br/>
对变量的引用，将在其中存储正在加载的永久性数据的版本号。

*dwVersionDefault*<br/>
控件的当前版本号。

*bConvert*<br/>
指示是否将永久性数据转换为当前版本，或将其保留为加载的同一版本。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0。

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange：： GetVersion

调用此函数可检索控件的版本号。

```
DWORD GetVersion();
```

### <a name="return-value"></a>返回值

控件的版本号。

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange：： IsAsynchronous

确定是否异步完成属性交换。

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>返回值

如果异步交换属性，则返回 TRUE; 否则返回 FALSE。

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange：： IsLoading

调用此函数可确定是否将属性加载到控件或将其保存。

```
BOOL IsLoading();
```

### <a name="return-value"></a>返回值

如果正在加载属性，则为非零值;否则为0。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleControl：:D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
