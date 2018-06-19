---
title: OLE 控件的持久性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e84e26bae83bd131b53d10e4561ddb60854a8a5e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378329"
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
  
 此外，还提供了 `AfxOleTypeMatchGuid` 全局函数来测试 `TYPEDESC` 与给定 GUID 是否匹配。  
  
##  <a name="px_blob"></a>  PX_Blob  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化存储二进制大型对象 (BLOB) 数据的属性。  
  
```  
 
BOOL  
PX_Blob(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    HGLOBAL& 
hBlob  ,  
    HGLOBAL 
hBlobDefault  
= NULL);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `hBlob`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `hBlobDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 属性的值将无法读取或写入到引用的变量`hBlob`适当。 此变量应初始化为**NULL**在最初调用之前`PX_Blob`第一次 （通常情况下，这可以在控件的构造函数）。 如果`hBlobDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的初始化或序列化过程失败，则使用此值。  
  
 句柄`hBlob`和`hBlobDefault`参考包含以下的内存块：  
  
-   A`DWORD`其中包含之后的二进制数据的长度，以字节为单位后, 跟来  
  
-   包含实际的二进制数据的内存块。  
  
 请注意，`PX_Blob`将分配内存，使用 Windows [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) API，在加载 BLOB 类型属性时。 你负责释放此内存。 因此，应调用你的控件的析构函数[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)句柄以释放 BLOB 类型的任何属性上向上分配给控件的任何内存。  
  
##  <a name="px_bool"></a>  PX_Bool  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**BOOL**。  
  
```  
 
BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& bValue);

BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& 
bValue  ,  
    BOOL bDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `bValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `bDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 属性的值将无法读取或写入到引用的变量`bValue`适当。 如果`bDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_color"></a>  PX_Color  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**OLE_COLOR**。  
  
```  
 
BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& 
clrValue  ,  
    OLE_COLOR 
clrDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `clrValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `clrDefault`  
 由控件开发人员定义的属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 属性的值将无法读取或写入到引用的变量`clrValue`适当。 如果`clrDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_currency"></a>  PX_Currency  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**货币**。  
  
```  
 
BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& cyValue);

BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& 
cyValue  ,  
    CY cyDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `cyValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `cyDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 属性的值将无法读取或写入到引用的变量`cyValue`适当。 如果`cyDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_datapath"></a>  PX_DataPath  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的数据路径属性[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)。  
  
```  
 
BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    LPCTSTR 
pszPropName,  
    CDataPathProperty& dataPathProperty);

BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    CDataPathProperty& dataPathProperty);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `dataPathProperty`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 数据路径属性实现异步控件属性。 属性的值将无法读取或写入到引用的变量`dataPathProperty`适当。  
  
##  <a name="px_double"></a>  PX_Double  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**double**。  
  
```  
 
BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& doubleValue);

BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& 
doubleValue  ,  
    double doubleDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `doubleValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `doubleDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`doubleValue`适当。 如果`doubleDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_font"></a>  PX_Font  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型字体的属性。  
  
```  
 
BOOL  
PX_Font(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CFontHolder& 
font  ,  
    const 
FONTDESC  
FAR* 
pFontDesc  
= 
NULL,  
    LPFONTDISP 
pFontDispAmbient  
= NULL);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `font`  
 对引用`CFontHolder`包含字体属性的对象。  
  
 `pFontDesc`  
 指向的指针**FONTDESC**结构，它包含要初始化的这种情况中的字体属性的默认状态使用的值其中`pFontDispAmbient`是**NULL**。  
  
 `pFontDispAmbient`  
 指向的指针**IFontDisp**接口的一种字体用于初始化字体属性的默认状态。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入属性的值`font`、`CFontHolder`引用，在适当的时候。 如果`pFontDesc`和`pFontDispAmbient`指定，它们用于初始化属性的默认值，在需要时。 如果出于任何原因，控件的序列化过程失败，则使用这些值。 通常情况下，传递**NULL**为`pFontDesc`和返回的环境值`COleControl::AmbientFont`为`pFontDispAmbient`。 请注意，返回字体对象`COleControl::AmbientFont`必须通过调用释放**IFontDisp::Release**成员函数。  
  
##  <a name="px_float"></a>  PX_Float  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**float**。  
  
```  
 
BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& floatValue);

BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& 
floatValue  ,  
    float floatDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `floatValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `floatDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`floatValue`适当。 如果`floatDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_iunknown"></a>  PX_IUnknown  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化对象具有所表示的属性**IUnknown**-派生接口。  
  
```  
 
BOOL  
PX_IUnknown(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    LPUNKNOWN& 
pUnk  ,  
    REFIID 
iid  ,  
    LPUNKNOWN 
pUnkDefault  
= NULL);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 *pUnk*  
 对包含的接口的对象，表示的属性值的变量的引用。  
  
 `iid`  
 此接口 ID，指示由控件使用的属性对象的接口。  
  
 `pUnkDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值*pUnk*适当。 如果`pUnkDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_long"></a>  PX_Long  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**长**。  
  
```  
 
BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& lValue);

BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& 
lValue  ,  
    long lDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `lValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `lDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`lValue`适当。 如果`lDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_picture"></a>  PX_Picture  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化你的控件的图片属性。  
  
```  
 
BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& pict);

BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& 
pict  ,  
    CPictureHolder& pictDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `pict`  
 引用[CPictureHolder](../../mfc/reference/cpictureholder-class.md)对象属性的存储位置 （通常你的类的成员变量）。  
  
 `pictDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`pict`适当。 如果`pictDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_short"></a>  PX_Short  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**短**。  
  
```  
 
BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& sValue);

BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& 
sValue  ,  
    short sDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `sValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `sDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`sValue`适当。 如果`sDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_ulong"></a>  PX_ULong  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性**ULONG**。  
  
```  
 
BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& ulValue);

BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& 
ulValue  ,  
    long ulDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 正在交换的属性名称。  
  
 `ulValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `ulDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`ulValue`适当。 如果`ulDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_ushort"></a>  PX_UShort  
 调用此函数在控件的`DoPropExchange`成员函数，以便序列化或初始化类型的属性`unsigned`**短**。  
  
```  
 
BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& usValue);

BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& 
usValue  ,  
    USHORT usDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 正在交换的属性名称。  
  
 *usValue*  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 *usDefault*  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值*usValue*适当。 如果*usDefault*指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_string"></a>  PXstring  
 调用此函数在控件的**DoPropExchange**成员函数，以便序列化或初始化字符的字符串属性。  
  
```  
 
BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& strValue);

BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& 
strValue  ,  
    CString strDefault);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `pszPropName`  
 要交换的属性的名称。  
  
 `strValue`  
 存储属性变量的引用 （通常你的类的成员变量）。  
  
 `strDefault`  
 属性的默认值。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 读取或写入变量引用的属性的值`strValue`适当。 如果`strDefault`指定，它将用作该属性的默认值。 如果出于任何原因，控件的序列化过程失败，则使用此值。  
  
##  <a name="px_vbxfontconvert"></a>  PX_VBXFontConvert  
 调用此函数在控件的`DoPropExchange`成员函数以通过转换将 VBX 控件的字体相关的属性初始化字体属性。  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>参数  
 `pPX`  
 指向[CPropExchange](../../mfc/reference/cpropexchange-class.md)对象 (通常作为参数传递给传递`DoPropExchange`)。  
  
 `font`  
 将包含转换后的 VBX 字体相关属性的 OLE 控件字体属性。  
  
### <a name="return-value"></a>返回值  
 如果 exchange 成功; 则为非 0如果不成功，则为 0。  
  
### <a name="remarks"></a>备注  
 仅设计为将 VBX 控件的直接替换 OLE 控件才应使用此函数。 当 Visual Basic 开发环境将转换包含将 VBX 控件使用相应替换 OLE 控件的窗体时，它将调用控件的**IDataObject::SetData**函数，传递属性中的设置，包含将 VBX 控件的属性数据。 此操作，反过来，导致该控件的`DoPropExchange`要调用函数。 `DoPropExchange` 可以调用`PX_VBXFontConvert`用于将 VBX 控件的字体相关属性转换 (例如，"字体名称，""FontSize，"，依此类推) 到 OLE 控件的字体属性的相应组件。  
  
 `PX_VBXFontConvert` 应仅调用控件实际上当转换从 VBX 窗体应用程序时。 例如：  
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
