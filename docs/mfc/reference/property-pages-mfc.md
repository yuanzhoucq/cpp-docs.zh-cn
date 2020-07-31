---
title: 属性页 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 9689d511760752903b83b34199fb035c0e7a8d37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214043"
---
# <a name="property-pages-mfc"></a>属性页 (MFC)

属性页通过支持基于对话框数据交换（DDX）的数据映射机制，在可自定义的图形界面中显示特定 OLE 控件属性的当前值，以便查看和编辑。

此数据映射机制将属性页控件映射到 OLE 控件的单个属性。 控件属性的值反映属性页控件的状态或内容。 属性页控件和属性之间的映射由属性页的成员函数中**DDP_** 函数调用指定 `DoDataExchange` 。 下面列出了一个**DDP_** 函数，这些函数可交换使用控件的属性页输入的数据：

### <a name="property-page-data-transfer"></a>属性页数据传输

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|将组合框中所选字符串的索引链接到控件的属性。|
|[DDP_CBString](#ddp_cbstring)|将组合框中选定的字符串链接到控件的属性。 选定的字符串可以以与属性的值相同的字母开头，但不需要完全匹配。|
|[DDP_CBStringExact](#ddp_cbstringexact)|将组合框中选定的字符串链接到控件的属性。 所选字符串和属性的字符串值必须完全匹配。|
|[DDP_Check](#ddp_check)|使用控件的属性链接控件的属性页中的复选框。|
|[DDP_LBIndex](#ddp_lbindex)|使用控件的属性将列表框中所选字符串的索引链接。|
|[DDP_LBString](#ddp_lbstring)|将列表框中选定的字符串链接到控件的属性。 选定的字符串可以以与属性的值相同的字母开头，但不需要完全匹配。|
|[DDP_LBStringExact](#ddp_lbstringexact)|将列表框中选定的字符串链接到控件的属性。 所选字符串和属性的字符串值必须完全匹配。|
|[DDP_PostProcessing](#ddp_postprocessing)|完成从控件传输属性值。|
|[DDP_Radio](#ddp_radio)|将控件的属性页中的单选按钮组链接到控件的属性。|
|[DDP_Text](#ddp_text)|使用控件的属性链接控件的属性页中的控件。 此函数处理多种不同类型的属性，例如 **`double`** 、 **`short`** 、BSTR 和 **`long`** 。|

有关 `DoDataExchange` 函数和属性页的详细信息，请参阅文章[ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。

下面是用于创建和管理 OLE 控件的属性页的宏列表：

### <a name="property-pages"></a>属性页

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|开始属性页 Id 列表。|
|[END_PROPPAGEIDS](#end_proppageids)|结束属性页 Id 列表。|
|[PROPPAGEID](#proppageid)|声明控件类的属性页。|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

在属性页的 `DoDataExchange` 函数中调用此函数可将整数属性与属性页的组合框中的当前选定项的索引同步。

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的组合框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的组合框控件交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBIndex` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

在属性页的函数中调用此函数 `DoDataExchange` 可将字符串属性的值与属性页上组合框中的当前所选内容同步。

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的组合框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的组合框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBString` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

在属性页的函数中调用此函数 `DoDataExchange` 可同步 string 属性的值，该属性与属性页上组合框中的当前选定内容完全匹配。

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的组合框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的组合框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBStringExact` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

在属性页的函数中调用此函数 `DoDataExchange` 可将属性的值与关联的属性页复选框控件同步。

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的复选框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的复选框控件交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_Check` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

在属性页的函数中调用此函数 `DoDataExchange` 可将 integer 属性的值与属性页上列表框中当前选定内容的索引同步。

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的列表框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的列表框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBIndex` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

在属性页的函数中调用此函数 `DoDataExchange` 可将字符串属性的值与属性页上的列表框中的当前所选内容同步。

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的列表框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的列表框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBString` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

在属性页的函数中调用此函数 `DoDataExchange` 可同步 string 属性的值，该属性与属性页上的列表框中的当前选定内容完全匹配。

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的列表框控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的列表框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBStringExact` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

在属性页的函数中调用此函数 `DoDataExchange` 可在保存属性值时，将属性值从属性页传输到控件。

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

### <a name="remarks"></a>备注

在所有数据交换函数都完成后，应调用此函数。 例如：

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

在控件的函数中调用此函数 `DoPropExchange` 可将属性的值与关联的属性页单选按钮控件同步。

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的单选按钮控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的单选按钮控件交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_Radio` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

在控件的函数中调用此函数 `DoDataExchange` 可将属性的值与关联的属性页控件同步。

```cpp
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*id*<br/>
与*pszPropName*指定的控件属性关联的控件的资源 ID。

*职员*<br/>
与由*id*指定的属性页控件和由*pszPropName*指定的属性关联的成员变量。

*pszPropName*<br/>
要与由*id*指定的控件交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_Text` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

开始定义控件的属性页 Id 列表。

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>参数

*class_name*<br/>
正在为其指定属性页的控件类的名称。

*计数*<br/>
控件类使用的属性页的数目。

### <a name="remarks"></a>备注

在定义类的成员函数的实现（.cpp）文件中，启动带有 BEGIN_PROPPAGEIDS 宏的属性页列表，然后为每个属性页添加宏项，并通过 END_PROPPAGEIDS 宏完成属性页列表。

有关属性页的详细信息，请参阅文章[ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

结束属性页 ID 列表的定义。

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
拥有属性页的控件类的名称。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID

添加 OLE 控件使用的属性页。

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>参数

*clsid*<br/>
属性页的唯一类 ID。

### <a name="remarks"></a>备注

必须在控件的实现文件中的 BEGIN_PROPPAGEIDS 和 END_PROPPAGEIDS 宏之间放置所有 PROPPAGEID 宏。

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
