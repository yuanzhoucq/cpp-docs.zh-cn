---
title: OLE 控件的持久性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373002"
---
# <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

OLE 控件的一项功能是属性持久化（或称为“序列化”），它允许 OLE 控件在文件或流中读取或写入属性值。 即使在容器应用程序销毁该控件之后，该应用程序仍可以使用序列化来存储控件的属性值。 之后，当创建控件的新实例时，OLE 控件的属性值可从文件或流中读取。

### <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

|||
|-|-|
|[PX_Blob](#px_blob)|交换存储二进制大型对象 (BLOB) 数据的控件属性。|
|[PX_Bool](#px_bool)|交换**BOOL**类型的控制属性。|
|[PX_Color](#px_color)|交换控件的颜色属性。|
|[PX_Currency](#px_currency)|交换**CY**类型的控件属性 。|
|[PX_DataPath](#px_datapath)|交换 `CDataPathProperty` 类型的控件属性。|
|[PX_Double](#px_double)|交换**双类型的**控制属性。|
|[PX_Font](#px_font)|交换控件的字体属性。|
|[PX_Float](#px_float)|交换类型**浮点**的控制属性。|
|[PX_IUnknown](#px_iunknown)|交换未定义类型的控件属性。|
|[PX_Long](#px_long)|交换**长**类型的控件属性 。|
|[PX_Picture](#px_picture)|交换控件的图片属性。|
|[PX_Short](#px_short)|交换**短类型的**控制属性 。|
|[PX_ULong](#px_ulong)|交换**ULONG**类型的控件属性 。|
|[PX_UShort](#px_ushort)|交换**USHORT**类型的控件属性 。|
|[PXstring](#px_string)|交换字符字符串控件属性。|
|[PX_VBXFontConvert](#px_vbxfontconvert)|将 VBX 控件的字体相关属性交换到 OLE 控件字体属性中。|

此外，`AfxOleTypeMatchGuid`还提供全局函数以测试 TYPEDESC 和给定 GUID 之间的匹配。

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化存储二进制大型对象 （BLOB） 数据的属性。

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*hBlob*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*hBlobDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值将酌情从*hBlob*引用的变量读取或写入。 在首次调用`PX_Blob`之前，应将此变量初始化为 NULL（通常，可以在控件的构造函数中完成）。 如果指定*了 hBlobDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的初始化或序列化过程失败，则使用此值。

句柄*hBlob*和*hBlobDefault*引用包含以下内容的内存块：

- DWORD，它包含以下二进制数据的长度（以字节为单位），紧接

- 包含实际二进制数据的内存块。

请注意，`PX_Blob`在加载 BLOB 类型属性时，将使用 Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) API 分配内存。 您负责释放此内存。 因此，控件的析构函数应在任何 BLOB 类型属性句柄上调用[GlobalFree，](/windows/win32/api/winbase/nf-winbase-globalfree)以释放分配给控件的任何内存。

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化 BOOL 类型的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*bValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*b默认*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值将酌情从*bValue*引用的变量读取或写入。 如果指定*bDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_color"></a><a name="px_color"></a>PX_Color

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化OLE_COLOR类型的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*clrValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*clrDefault*<br/>
属性的默认值，由控件开发人员定义。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值将酌情从*clrValue*引用的变量读取或写入。 如果指定*clrDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化类型**货币**的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*赛价值*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*cyDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值将酌情从*cyValue*引用的变量读取或写入。 如果指定*了 cyDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)类型的数据路径属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*数据路径属性*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

数据路径属性实现异步控制属性。 属性的值将酌情从*dataPathProperty*引用的变量读取或写入。

## <a name="px_double"></a><a name="px_double"></a>PX_Double

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化类型**为 double**的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*双值*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*双默认*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*doubleValue*引用的变量读取或写入。 如果指定*doubleDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_font"></a><a name="px_font"></a>PX_Font

在控件`DoPropExchange`的成员函数中调用此功能，以序列化或初始化类型字体的属性。

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*字体*<br/>
对包含字体属性`CFontHolder`的对象的引用。

*普丰德斯茨*<br/>
指向包含用于初始`FONTDESC`化字体属性的默认状态的值的结构的指针，在*pFontDispAmbient*为 NULL 的情况下。

*pFontDisp环境*<br/>
指向字体`IFontDisp`接口的指针，用于初始化字体属性的默认状态。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值在适当时从 读取或写入`font`引用`CFontHolder`。 如果指定*了 pFontDesc*和*pFontDispAmbient，* 则它们用于在需要时初始化属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用这些值。 通常，您传递*pFontDesc*的 NULL 和`COleControl::AmbientFont`*pFontDispAmbient*返回的环境值。 请注意，返回的`COleControl::AmbientFont`字体对象必须通过调用`IFontDisp::Release`成员功能来释放。

## <a name="px_float"></a><a name="px_float"></a>PX_Float

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化类型**浮点**的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*浮动值*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*浮动默认值*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*floatValue*引用的变量读取或写入。 如果指定*floatDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

在控件`DoPropExchange`的成员函数中调用此函数，以序列化或初始化由具有`IUnknown`派生接口的对象表示的属性。

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*朋 克*<br/>
引用包含表示属性值的对象的接口的变量。

*Iid*<br/>
指示控件使用属性对象的哪个接口的接口 ID。

*pUnkDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*pUnk*引用的变量读取或写入。 如果指定*了 pUnkDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_long"></a><a name="px_long"></a>PX_Long

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化**长**类型的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*lValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*l 默认*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*lValue*引用的变量读取或写入。 如果指定*了 lDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化控件的图片属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*图片*<br/>
引用存储属性的[CPictureHolder](../../mfc/reference/cpictureholder-class.md)对象（通常是类的成员变量）。

*图片默认*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*pict*引用的变量读取或写入。 如果指定*pictDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_short"></a><a name="px_short"></a>PX_Short

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化类型**短**的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*sValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*sDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*sValue*引用的变量读取或写入。 如果指定*了 sDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化**ULONG**类型的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*ulValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*ulDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*ulValue*引用的变量读取或写入。 如果指定*了 ulDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化**类型无符号短**的属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*usValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*我们默认*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*usValue*引用的变量读取或写入。 如果指定*了 UsDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="pxstring"></a><a name="px_string"></a>PXstring

在控件`DoPropExchange`的成员函数中调用此函数以序列化或初始化字符串属性。

```cpp
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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszProp名称*<br/>
要交换的属性的名称。

*strValue*<br/>
对存储属性的变量（通常是类的成员变量）的引用。

*strDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

属性的值根据需要从*strValue*引用的变量读取或写入。 如果指定*strDefault，* 它将用作属性的默认值。 如果由于任何原因，控件的序列化过程失败，则使用此值。

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

在控件`DoPropExchange`的成员函数中调用此功能，通过转换 VBX 控件的字体相关属性来初始化字体属性。

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*字体*<br/>
包含转换后的 VBX 字体相关属性的 OLE 控件的字体属性。

### <a name="return-value"></a>返回值

如果交换成功，则非零;0，如果不成功。

### <a name="remarks"></a>备注

此功能只能由设计为直接替换 VBX 控件的 OLE 控件使用。 当 Visual Basic 开发环境转换包含 VBX 控件的窗体以使用相应的替换 OLE 控件时，它将调用控件`IDataObject::SetData`的函数，传入包含 VBX 控件的属性数据的属性集中。 此操作反过来又会导致调用控件的功能`DoPropExchange`。 `DoPropExchange`可以调用`PX_VBXFontConvert`将 VBX 控件的字体相关属性（例如，"FontName"、"FontSize"等）转换为 OLE 控件的字体属性的相应组件。

`PX_VBXFontConvert`仅当控件实际从 VBX 窗体应用程序转换时，才应调用该控件。 例如：

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
