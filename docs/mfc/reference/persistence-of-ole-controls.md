---
title: OLE 控件的持久性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 42e70f9e48339eddb2a5af4fa288400cce01f490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502032"
---
# <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

OLE 控件的一项功能是属性持久化（或称为“序列化”），它允许 OLE 控件在文件或流中读取或写入属性值。 即使在容器应用程序销毁该控件之后，该应用程序仍可以使用序列化来存储控件的属性值。 之后，当创建控件的新实例时，OLE 控件的属性值可从文件或流中读取。

### <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

|||
|-|-|
|[PX_Blob](#px_blob)|交换存储二进制大型对象 (BLOB) 数据的控件属性。|
|[PX_Bool](#px_bool)|交换类型为**BOOL**的控件属性。|
|[PX_Color](#px_color)|交换控件的颜色属性。|
|[PX_Currency](#px_currency)|交换类型为**CY**的控件属性。|
|[PX_DataPath](#px_datapath)|交换 `CDataPathProperty` 类型的控件属性。|
|[PX_Double](#px_double)|交换类型为**double**的控件属性。|
|[PX_Font](#px_font)|交换控件的字体属性。|
|[PX_Float](#px_float)|交换**float**类型的控件属性。|
|[PX_IUnknown](#px_iunknown)|交换未定义类型的控件属性。|
|[PX_Long](#px_long)|交换**long**类型的控件属性。|
|[PX_Picture](#px_picture)|交换控件的图片属性。|
|[PX_Short](#px_short)|交换**short**类型的控件属性。|
|[PX_ULong](#px_ulong)|交换类型为**ULONG**的控件属性。|
|[PX_UShort](#px_ushort)|交换类型为**USHORT**的控件属性。|
|[PXstring](#px_string)|交换字符字符串控件属性。|
|[PX_VBXFontConvert](#px_vbxfontconvert)|将 VBX 控件的字体相关属性交换到 OLE 控件字体属性中。|

此外，还提供`AfxOleTypeMatchGuid`了全局函数来测试 TYPEDESC 和给定 GUID 之间的匹配。

##  <a name="px_blob"></a>  PX_Blob

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化存储二进制大型对象（BLOB）数据的属性。

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*hBlob*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*hBlobDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从*hBlob*引用的变量读取或写入属性的值。 第一次调用`PX_Blob`之前，应将此变量初始化为 NULL （通常情况下，可以在控件的构造函数中完成此操作）。 如果指定了*hBlobDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的初始化或序列化进程失败，则使用此值。

句柄*hBlob*和*hBlobDefault*指的是内存块，其中包含以下内容：

- 一个 DWORD，其中包含后面紧跟的二进制数据的长度（以字节为单位）

- 包含实际二进制数据的内存块。

请注意，在加载 BLOB 类型属性时 ，`PX_Blob`将使用Windows[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)API分配内存。 你负责释放此内存。 因此，控件的析构函数应调用任何 BLOB 类型属性句柄上的[GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) ，以释放分配给控件的任何内存。

##  <a name="px_bool"></a>  PX_Bool

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化 BOOL 类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*bValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*bDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从*bValue*引用的变量读取或写入属性的值。 如果指定了*bDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_color"></a>  PX_Color

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化 OLE_COLOR 类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*clrValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*clrDefault*<br/>
属性的默认值，由控件开发人员定义。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从*clrValue*引用的变量读取或写入属性的值。 如果指定了*clrDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_currency"></a>  PX_Currency

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化**货币**类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*cyValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*cyDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从*cyValue*引用的变量读取或写入属性的值。 如果指定了*cyDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_datapath"></a>  PX_DataPath

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)类型的数据路径属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*dataPathProperty*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

数据路径属性实现异步控件属性。 根据需要，将从*dataPathProperty*引用的变量读取或写入属性的值。

##  <a name="px_double"></a>  PX_Double

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化**double**类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*doubleValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*doubleDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*doubleValue*引用的变量读取或写入属性的值。 如果指定了*doubleDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_font"></a>  PX_Font

在控件的`DoPropExchange`成员函数中调用此函数，以便序列化或初始化类型字体的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*font*<br/>
对包含 font 属性`CFontHolder`的对象的引用。

*pFontDesc*<br/>
指向`FONTDESC`结构的指针，该结构包含在初始化 font 属性的默认状态时要使用的值（在*pFontDispAmbient*为 NULL 的情况下）。

*pFontDispAmbient*<br/>
一个指针，指向`IFontDisp`用于初始化 font 属性的默认状态的字体的接口。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

适当时，属性的值将在`font` `CFontHolder`引用中进行读取或写入。 如果指定了*pFontDesc*和*pFontDispAmbient* ，则在需要时，它们用于初始化属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用这些值。 通常，为*pFontDesc*传递 NULL，并`COleControl::AmbientFont`为*pFontDispAmbient*传递返回的环境值。 请注意，由返回`COleControl::AmbientFont`的 font 对象必须通过调用`IFontDisp::Release`成员函数来释放。

##  <a name="px_float"></a>  PX_Float

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化**float**类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*floatValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*floatDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*floatValue*引用的变量读取或写入属性的值。 如果指定了*floatDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_iunknown"></a>PX_IUnknown

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化`IUnknown`具有派生接口的对象所表示的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*pUnk*<br/>
对变量的引用，该变量包含表示属性值的对象的接口。

*iid*<br/>
一个接口 ID，指示控件使用的属性对象的接口。

*pUnkDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*pUnk*引用的变量读取或写入属性的值。 如果指定了*pUnkDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_long"></a>  PX_Long

在控件的`DoPropExchange`成员函数中调用此函数，以便序列化或初始化**long**类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*lValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*lDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*lValue*引用的变量读取或写入属性的值。 如果指定了*lDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_picture"></a>  PX_Picture

在控件的`DoPropExchange`成员函数中调用此函数，以便序列化或初始化控件的图片属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*pict*<br/>
对存储属性的[CPictureHolder](../../mfc/reference/cpictureholder-class.md)对象的引用（通常为类的成员变量）。

*pictDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*pict*引用的变量读取或写入属性的值。 如果指定了*pictDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_short"></a>  PX_Short

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化**short**类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*sValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*sDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*sValue*引用的变量读取或写入属性的值。 如果指定了*sDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_ulong"></a>  PX_ULong

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化类型为**ULONG**的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
正在交换的属性的名称。

*ulValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*ulDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*ulValue*引用的变量读取或写入属性的值。 如果指定了*ulDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_ushort"></a>  PX_UShort

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化类型为**short**的类型的属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
正在交换的属性的名称。

*usValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*usDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*usValue*引用的变量读取或写入属性的值。 如果指定了*usDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_string"></a>  PXstring

在控件的`DoPropExchange`成员函数中调用此函数，以序列化或初始化字符串属性。

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
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*pszPropName*<br/>
要交换的属性的名称。

*strValue*<br/>
对存储属性的变量的引用（通常为类的成员变量）。

*strDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从*strValue*引用的变量读取或写入属性的值。 如果指定了*strDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

##  <a name="px_vbxfontconvert"></a>  PX_VBXFontConvert

通过转换 VBX 控件的字体相关`DoPropExchange`属性，在控件的成员函数中调用此函数以初始化字体属性。

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>参数

*pPX*<br/>
指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象的指针（通常作为参数传递给`DoPropExchange`）。

*font*<br/>
OLE 控件的 "字体" 属性，将包含已转换的 VBX 字体相关属性。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

此函数应仅由设计为 VBX 控件的直接替换的 OLE 控件使用。 当 Visual Basic 开发环境转换包含 VBX 控件的窗体以使用相应的替换 OLE 控件时，它将调用控件的`IDataObject::SetData`函数，并传入包含 VBX 控件的属性数据的属性集。 此操作反过来会导致调用控件的`DoPropExchange`函数。 `DoPropExchange`可以调用`PX_VBXFontConvert` ，将 VBX 控件的字体相关属性（例如，"FontName"、"FontSize" 等）转换为 OLE 控件的 "字体" 属性的相应组件。

`PX_VBXFontConvert`只应在实际从 VBX 窗体应用程序转换控件时调用。 例如:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>请参阅

[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)
