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
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363969"
---
# <a name="cpropexchange-class"></a>CPropExchange 类

支持 OLE 控件持久性的实现。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPropExchange：：交换BlobProp](#exchangeblobprop)|交换二进制大型对象 （BLOB） 属性。|
|[CPropExchange：：交换方普罗普](#exchangefontprop)|交换字体属性。|
|[CPropExchange：：交换持久](#exchangepersistentprop)|在控件和文件之间交换属性。|
|[CPropExchange：交换](#exchangeprop)|交换任何内置类型的属性。|
|[CPropExchange：交换版本](#exchangeversion)|交换 OLE 控件的版本号。|
|[CPropExchange：获取版本](#getversion)|检索 OLE 控件的版本号。|
|[CPropExchange：是同步的](#isasynchronous)|确定属换是否异步完成。|
|[CPropExchange：正在加载](#isloading)|指示属性是加载到控件中还是从控件中保存。|

## <a name="remarks"></a>备注

`CPropExchange`没有基类。

建立财产交换的上下文和方向。

持久性是控件本身和介质之间的状态信息（通常由其属性表示）的交换。

框架构造从`CPropExchange`通知 OLE 控件的属性将从持久存储加载或存储到持久存储时派生的对象。

框架将指向此`CPropExchange`对象的指针传递给控件的`DoPropExchange`函数。 如果使用向导为控件创建启动文件，则控件的`DoPropExchange`函数将调用`COleControl::DoPropExchange`。 基类版本交换控件的股票属性;修改派生类的版本以交换已添加到控件的属性。

`CPropExchange`可用于在加载或创建控件时序列化控件的属性或初始化控件的属性。 和`ExchangeProp``ExchangeFontProp`成员函数`CPropExchange`能够将属性存储到并从不同的媒体加载它们。

有关 使用`CPropExchange`的详细信息，请参阅文章[MFC ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CPropExchange`

## <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange：：交换BlobProp

序列化存储二进制大型对象 （BLOB） 数据的属性。

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>参数

*pszProp名称*<br/>
要交换的属性的名称。

*phBlob*<br/>
指向指向属性存储位置的变量的指针（变量通常是类的成员）。

*hBlobDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值从*phBlob*引用的变量读取或写入（视情况而定）。 如果指定*了 hBlobDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化失败，则使用此值。

函数`CArchivePropExchange::ExchangeBlobProp`，`CResetPropExchange::ExchangeBlobProp`并`CPropsetPropExchange::ExchangeBlobProp`重写此纯虚拟函数。

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange：：交换方普罗普

在存储介质和控件之间交换字体属性。

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>参数

*pszProp名称*<br/>
要交换的属性的名称。

*字体*<br/>
对包含字体属性的[CFontHolder](../../mfc/reference/cfontholder-class.md)对象的引用。

*普丰德斯茨*<br/>
指向[FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)结构的指针，其中包含用于在*pFontDispAmbient*为 NULL 时初始化字体属性的默认状态的值。

*pFontDisp环境*<br/>
指向用于初始化`IFontDisp`字体属性的默认状态的字体接口的指针。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

如果字体属性从介质加载到控件，则从介质中检索字体的特征，并且`CFontHolder`*使用字体*引用的对象进行初始化。 如果正在存储字体属性，则字体对象中的特征将写入介质。

函数`CArchivePropExchange::ExchangeFontProp`，`CResetPropExchange::ExchangeFontProp`并`CPropsetPropExchange::ExchangeFontProp`重写此纯虚拟函数。

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange：：交换持久

在控件和文件之间交换属性。

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>参数

*pszProp名称*<br/>
要交换的属性的名称。

*普恩克*<br/>
指向包含指向属性接口的指针的`IUnknown`变量的指针（此变量通常是类的成员）。

*Iid*<br/>
控件将使用的属性上的接口的接口的接口 ID。

*pUnkDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

如果属性从文件加载到控件，则从文件创建和初始化该属性。 如果正在存储该属性，则其值将写入文件。

函数`CArchivePropExchange::ExchangePersistentProp`，`CResetPropExchange::ExchangePersistentProp`并`CPropsetPropExchange::ExchangePersistentProp`重写此纯虚拟函数。

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange：交换

在存储介质和控制之间交换属性。

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>参数

*pszProp名称*<br/>
要交换的属性的名称。

*vtProp*<br/>
指定要交换的属性类型的符号。 可能的值包括：

|符号|属性类型|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**长**|
|VT_BOOL|**Bool**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**浮动**|
|VT_R8|**double**|

*pvProp*<br/>
指向属性值的指针。

*pvDefault*<br/>
指向属性的默认值的指针。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

如果属性从介质加载到控件，则从介质检索该属性的值并存储在*pvProp*指向的对象中。 如果属性被存储到介质，*则 pvProp*指向的对象的值将写入介质。

函数`CArchivePropExchange::ExchangeProp`，`CResetPropExchange::ExchangeProp`并`CPropsetPropExchange::ExchangeProp`重写此纯虚拟函数。

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange：交换版本

由框架调用来处理版本号的持久性。

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>参数

*dwVersionLoaded*<br/>
引用将存储要加载的持久数据的版本号的变量。

*dwVersionDefault*<br/>
控件的当前版本号。

*b转换*<br/>
指示是将持久性数据转换为当前版本，还是将其保留在加载的相同版本。

### <a name="return-value"></a>返回值

如果函数成功，则非零;0 否则。

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange：获取版本

调用此函数以检索控件的版本号。

```
DWORD GetVersion();
```

### <a name="return-value"></a>返回值

控件的版本号。

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange：是同步的

确定属换是否异步完成。

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>返回值

如果以异步方式交换属性，则返回 TRUE，否则为 FALSE。

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange：正在加载

调用此函数以确定属性是加载到控件还是从控件中保存。

```
BOOL IsLoading();
```

### <a name="return-value"></a>返回值

如果正在加载属性，则非零;否则 0。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleControl：:DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
