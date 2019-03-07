---
title: OLE 控件的持久性
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.ole
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: b8bcba63c8e09873fe7f30e4fd07d652850be1f3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299642"
---
# <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

OLE 控件的一项功能是属性持久化（或称为“序列化”），它允许 OLE 控件在文件或流中读取或写入属性值。 即使在容器应用程序销毁该控件之后，该应用程序仍可以使用序列化来存储控件的属性值。 之后，当创建控件的新实例时，OLE 控件的属性值可从文件或流中读取。

### <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

|||
|-|-|
|[PX_Blob](#px_blob)|交换存储二进制大型对象 (BLOB) 数据的控件属性。|
|[PX_Bool](#px_bool)|交换类型的控件属性**BOOL**。|
|[PX_Color](#px_color)|交换控件的颜色属性。|
|[PX_Currency](#px_currency)|交换类型的控件属性**CY**。|
|[PX_DataPath](#px_datapath)|交换 `CDataPathProperty` 类型的控件属性。|
|[PX_Double](#px_double)|交换类型的控件属性**double**。|
|[PX_Font](#px_font)|交换控件的字体属性。|
|[PX_Float](#px_float)|交换类型的控件属性**float**。|
|[PX_IUnknown](#px_iunknown)|交换未定义类型的控件属性。|
|[PX_Long](#px_long)|交换类型的控件属性**长**。|
|[PX_Picture](#px_picture)|交换控件的图片属性。|
|[PX_Short](#px_short)|交换类型的控件属性**短**。|
|[PX_ULong](#px_ulong)|交换类型的控件属性**ULONG**。|
|[PX_UShort](#px_ushort)|交换类型的控件属性**USHORT**。|
|[PXstring](#px_string)|交换字符字符串控件属性。|
|[PX_VBXFontConvert](#px_vbxfontconvert)|将 VBX 控件的字体相关属性交换到 OLE 控件字体属性中。|

此外，`AfxOleTypeMatchGuid`提供全局函数来测试 TYPEDESC 与给定的 GUID 相匹配。

##  <a name="px_blob"></a>  PX_Blob

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化存储二进制大型对象 (BLOB) 数据的属性。

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*hBlob*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*hBlobDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

属性的值将无法读取或写入到由所引用的变量*hBlob*根据。 最初调用之前，应将此变量初始化为 NULL`PX_Blob`第一次 （通常情况下，这可以在控件的构造函数中）。 如果*hBlobDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的初始化或序列化进程将失败，则使用此值。

句柄*hBlob*并*hBlobDefault*到其中包含以下内存块，请参阅：

- 一个 dword 值，其中包含之后的二进制数据的长度，以字节为单位后, 跟来

- 包含实际的二进制数据的内存块。

请注意，`PX_Blob`将分配内存，使用 Windows [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) API，当加载 BLOB 类型属性。 你负责释放此内存。 因此，您的控件的析构函数应调用[GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree)句柄，以释放 BLOB 类型的任何属性上向上分配到控件中的任何内存。

##  <a name="px_bool"></a>  PX_Bool

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型 BOOL 的属性。

```
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*bValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*bDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

属性的值将无法读取或写入到由所引用的变量*bValue*根据。 如果*bDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_color"></a>  PX_Color

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型 OLE_COLOR 的属性。

```
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*clrValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*clrDefault*<br/>
由控件开发人员定义的属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

属性的值将无法读取或写入到由所引用的变量*clrValue*根据。 如果*clrDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_currency"></a>  PX_Currency

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**货币**。

```
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*cyValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*cyDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

属性的值将无法读取或写入到由所引用的变量*cyValue*根据。 如果*cyDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_datapath"></a>  PX_DataPath

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的数据路径属性[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)。

```
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*dataPathProperty*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

数据路径属性实现异步控件属性。 属性的值将无法读取或写入到由所引用的变量*dataPathProperty*根据。

##  <a name="px_double"></a>  PX_Double

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**double**。

```
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*doubleValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*doubleDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*doubleValue*根据。 如果*doubleDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_font"></a>  PX_Font

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型字体的属性。

```
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*font*<br/>
对引用`CFontHolder`对象，其中包含字体属性。

*pFontDesc*<br/>
一个指向`FONTDESC`结构，它包含要初始化的字体属性，在这种情况中的默认状态使用的值， *pFontDispAmbient*为 NULL。

*pFontDispAmbient*<br/>
一个指向`IFontDisp`接口的一种字体用于初始化的字体属性的默认状态。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入属性的值`font`、`CFontHolder`引用，在适当的时候。 如果*pFontDesc*并*pFontDispAmbient*指定，它们用于在需要时初始化该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用这些值。 通常情况下，传递 NULL， *pFontDesc*返回的环境值`COleControl::AmbientFont`有关*pFontDispAmbient*。 请注意，返回字体对象`COleControl::AmbientFont`必须通过调用释放`IFontDisp::Release`成员函数。

##  <a name="px_float"></a>  PX_Float

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**float**。

```
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*floatValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*floatDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*floatValue*根据。 如果*floatDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_iunknown"></a>  PX_IUnknown

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化对象具有所表示的属性`IUnknown`-派生接口。

```
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*pUnk*<br/>
对包含该对象表示的属性值的接口的变量的引用。

*iid*<br/>
接口 ID，指示由控件使用的属性对象的接口。

*pUnkDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*pUnk*根据。 如果*pUnkDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_long"></a>  PX_Long

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**长**。

```
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*lValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*lDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*左值*根据。 如果*lDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_picture"></a>  PX_Picture

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化您的控件的图片属性。

```
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*pict*<br/>
引用[CPictureHolder](../../mfc/reference/cpictureholder-class.md)对象属性的存储位置 （通常在类的成员变量）。

*pictDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*pict*根据。 如果*pictDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_short"></a>  PX_Short

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**短**。

```
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*sValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*sDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*sValue*根据。 如果*sDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_ulong"></a>  PX_ULong

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**ULONG**。

```
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性名称。

*ulValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*ulDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*ulValue*根据。 如果*ulDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_ushort"></a>  PX_UShort

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化类型的属性**unsigned short**。

```
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性名称。

*usValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*usDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*usValue*根据。 如果*usDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_string"></a>  PXstring

调用此函数在控件内的`DoPropExchange`成员函数要序列化或初始化字符字符串属性。

```
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*pszPropName*<br/>
正在交换的属性的名称。

*strValue*<br/>
该属性的存储位置的变量的引用 （通常在类的成员变量）。

*strDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

读取或写入变量引用的属性的值*strValue*根据。 如果*strDefault*指定，它将用作该属性的默认值。 如果出于任何原因，该控件的序列化进程将失败，则使用此值。

##  <a name="px_vbxfontconvert"></a>  PX_VBXFontConvert

调用此函数在控件内的`DoPropExchange`成员函数以初始化通过转换将 VBX 控件的字体相关属性的字体属性。

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给`DoPropExchange`)。

*font*<br/>
将包含转换后的 VBX 与字体相关属性的 OLE 控件字体属性。

### <a name="return-value"></a>返回值

如果交换成功，则非零值如果不成功，则为 0。

### <a name="remarks"></a>备注

此函数应使用仅由 OLE 控件的设计为将 VBX 控件的直接替代品。 当 Visual Basic 开发环境将包含该 VBX 控件使用相应替换 OLE 控件的窗体时，它将调用控件的`IDataObject::SetData`函数，并传入包含该 VBX 控件的属性数据的属性集。 此操作，又会导致该控件的`DoPropExchange`要调用的函数。 `DoPropExchange` 可以调用`PX_VBXFontConvert`将 VBX 控件的字体相关属性 (例如，"字体名称，""FontSize，"，等等) 到 OLE 控件的字体属性的对应分量。

`PX_VBXFontConvert` 时，应仅调用该控件实际上正在转换从 VBX 窗体应用程序。 例如：

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
