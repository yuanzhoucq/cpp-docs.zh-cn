---
title: 属性页 (MFC)
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 4f8e56ed4be6bf4c7a5283894493ee46c4ed2ff4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620904"
---
# <a name="property-pages-mfc"></a>属性页 (MFC)

属性页在用于查看和编辑通过支持基于对话框数据交换 (DDX) 的数据映射机制可自定义的图形界面中显示特定 OLE 控件属性的当前值。

此数据映射机制将映射到 OLE 控件的各个属性的属性页控件。 控件属性的值反映了状态或属性页控件的内容。 通过指定属性页控件和属性之间的映射**DDP_** 函数将调用在属性页`DoDataExchange`成员函数。 以下是一系列**DDP_** 交换使用您的控件的属性页的格式输入的数据的函数：

### <a name="property-page-data-transfer"></a>属性页数据传输

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|链接具有控件的属性的组合框中的所选的字符串的索引。|
|[DDP_CBString](#ddp_cbstring)|链接具有控件的属性的组合框中所选的字符串。 所选的字符串可以以属性的值相同的字母开头，但不需要完全匹配。|
|[DDP_CBStringExact](#ddp_cbstringexact)|链接具有控件的属性的组合框中所选的字符串。 所选的字符串和属性的字符串值必须完全匹配。|
|[DDP_Check](#ddp_check)|链接控件的属性的控件的属性页中的复选框。|
|[DDP_LBIndex](#ddp_lbindex)|链接具有控件的属性的列表框中的所选的字符串的索引。|
|[DDP_LBString](#ddp_lbstring)|链接具有控件的属性的列表框中所选的字符串。 所选的字符串可以以属性的值相同的字母开头，但需要完全匹配它。|
|[DDP_LBStringExact](#ddp_lbstringexact)|链接具有控件的属性的列表框中所选的字符串。 所选的字符串和属性的字符串值必须完全匹配。|
|[DDP_PostProcessing](#ddp_postprocessing)|完成从您的控件的属性值的传输。|
|[DDP_Radio](#ddp_radio)|与控件的属性的控件的属性页中的单选按钮组的链接。|
|[DDP_Text](#ddp_text)|与控件的属性的控件的属性页中将控件链接。 此函数处理多个不同类型的属性，如**双**，**短**，BSTR，以及**长**。|

有关详细信息`DoDataExchange`函数和属性页，请参阅文章[ActiveX 控件： 属性页](../../mfc/mfc-activex-controls-property-pages.md)。

下面是用于创建和管理 OLE 控件的属性页的宏的列表：

### <a name="property-pages"></a>属性页

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|开始属性页 Id 的列表。|
|[END_PROPPAGEIDS](#end_proppageids)|结束属性页 Id 的列表。|
|[PROPPAGEID](#proppageid)|声明控件类的属性页。|

##  <a name="ddp_cbindex"></a>  DDP_CBIndex

在属性页的 `DoDataExchange` 函数中调用此函数可将整数属性与属性页的组合框中的当前选定项的索引同步。

```
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
资源 ID 的组合框控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的组合框控件交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBIndex` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_cbstring"></a>  DDP_CBString

在属性页中调用此函数`DoDataExchange`函数用于将字符串属性的值与属性页上的组合框中当前所选内容同步。

```
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
资源 ID 的组合框控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的组合框字符串进行交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBString` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_cbstringexact"></a>  DDP_CBStringExact

在属性页中调用此函数`DoDataExchange`函数来同步完全匹配的属性页上的组合框中当前所选内容的字符串属性的值。

```
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
资源 ID 的组合框控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的组合框字符串进行交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBStringExact` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_check"></a>  DDP_Check

在属性页中调用此函数`DoDataExchange`函数关联的属性页复选框控件与同步的属性值。

```
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
与指定的控件属性关联的复选框控件的资源 ID *pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的复选框控件交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_Check` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_lbindex"></a>  DDP_LBIndex

在属性页中调用此函数`DoDataExchange`函数与进行同步的一个整数属性的值的属性页上的列表框中的当前选定的索引。

```
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
资源 ID 的列表框控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的列表框中字符串进行交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBIndex` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_lbstring"></a>  DDP_LBString

在属性页中调用此函数`DoDataExchange`函数用于将字符串属性的值与属性页上的列表框中当前所选内容同步。

```
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
资源 ID 的列表框控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的列表框中字符串进行交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBString` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_lbstringexact"></a>  DDP_LBStringExact

在属性页中调用此函数`DoDataExchange`函数来同步完全匹配的属性页上的列表框中当前所选内容的字符串属性的值。

```
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
资源 ID 的列表框控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的列表框中字符串进行交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBStringExact` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_postprocessing"></a>  DDP_PostProcessing

在属性页中调用此函数`DoDataExchange`函数完成时保存属性值的属性值的属性页传输到您的控件。

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

### <a name="remarks"></a>备注

在所有数据交换函数执行完成都后，应调用此函数。 例如：

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_radio"></a>  DDP_Radio

调用此函数在控件的`DoPropExchange`函数与关联的属性页单选按钮控件同步的属性值。

```
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
资源 ID 的单选按钮控件与指定的控件属性相关联*pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的单选按钮控件交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_Radio` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="ddp_text"></a>  DDP_Text

调用此函数在控件的`DoDataExchange`函数与关联的属性页控件同步的属性值。

```
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
与指定的控件属性关联的控件的资源 ID *pszPropName*。

*member*<br/>
与指定的属性页控件关联的成员变量*id*和指定的属性*pszPropName*。

*pszPropName*<br/>
要与指定的控件进行交换的控件属性的属性名称*id*。

### <a name="remarks"></a>备注

应在相应的 `DDX_Text` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS

开始控件的属性页 Id 列表的定义。

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>参数

*class_name*<br/>
正在指定的属性页的控件类的名称。

*count*<br/>
使用的控件类的属性页的数目。

### <a name="remarks"></a>备注

在实现 (.cpp) 文件中定义您的类的成员函数，属性页列表开头 BEGIN_PROPPAGEIDS 宏，则为每个属性页中，添加宏条目并完成属性页列表与 END_PROPPAGEIDS宏。

属性页的详细信息，请参阅文章[ActiveX 控件： 属性页](../../mfc/mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="end_proppageids"></a>  END_PROPPAGEIDS

结束在属性页 ID 列表中定义。

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
拥有属性页的控件类的名称。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="proppageid"></a>  PROPPAGEID

将使用的属性页添加 OLE 控件。

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>参数

*clsid*<br/>
属性页的唯一类 ID。

### <a name="remarks"></a>备注

必须将所有 PROPPAGEID 宏都放置控件的实现文件中的 BEGIN_PROPPAGEIDS 和 END_PROPPAGEIDS 宏之间。

### <a name="requirements"></a>要求

  **标头**afxctl.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
