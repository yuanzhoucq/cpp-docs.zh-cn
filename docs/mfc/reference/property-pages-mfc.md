---
title: 属性页 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 1064cd99d1820ae8865fa632c3097441172c78c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372995"
---
# <a name="property-pages-mfc"></a>属性页 (MFC)

属性页通过支持基于对话框数据交换 （DDX） 的数据映射机制，在可自定义的图形界面中显示特定 OLE 控件属性的当前值，以便查看和编辑。

此数据映射机制将属性页控件映射到 OLE 控件的各个属性。 控件属性的值反映属性页控件的状态或内容。 属性页控件和属性之间的映射由属性页`DoDataExchange`成员函数中**DDP_** 函数调用指定。 以下是交换使用控件的属性页输入的数据**的DDP_** 函数的列表：

### <a name="property-page-data-transfer"></a>属性页数据传输

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|将所选字符串的索引链接到具有控件属性的组合框中。|
|[DDP_CBString](#ddp_cbstring)|将所选字符串链接到组合框中具有控件的属性。 所选字符串可以以与属性值相同的字母开头，但不需要与属性的值完全匹配。|
|[DDP_CBStringExact](#ddp_cbstringexact)|将所选字符串链接到组合框中具有控件的属性。 所选字符串和属性的字符串值必须完全匹配。|
|[DDP_Check](#ddp_check)|将控件的属性页中的复选框与控件的属性链接。|
|[DDP_LBIndex](#ddp_lbindex)|在列表框中链接所选字符串的索引，并带有控件的属性。|
|[DDP_LBString](#ddp_lbstring)|将所选字符串链接到列表框中具有控件的属性。 所选字符串可以以与属性值相同的字母开头，但不必完全匹配它。|
|[DDP_LBStringExact](#ddp_lbstringexact)|将所选字符串链接到列表框中具有控件的属性。 所选字符串和属性的字符串值必须完全匹配。|
|[DDP_PostProcessing](#ddp_postprocessing)|完成从控件转移属性值。|
|[DDP_Radio](#ddp_radio)|将控件的属性页中的单选按钮组与控件的属性链接。|
|[DDP_Text](#ddp_text)|将控件的属性页中的控件与控件的属性链接。 此函数处理几种不同类型的属性，如**双**、**短**、BSTR 和**长**。|

有关`DoDataExchange`函数和属性页的详细信息，请参阅[文章 ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。

以下是用于创建和管理 OLE 控件的属性页的宏列表：

### <a name="property-pages"></a>属性页

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|开始属性页 I 的列表。|
|[END_PROPPAGEIDS](#end_proppageids)|结束属性页 I 的列表。|
|[PROPPAGEID](#proppageid)|声明控件类的属性页。|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

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
与*pszPropName*指定的控件属性关联的组合框控件的资源 ID。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的组合框控件交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBIndex` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

在属性页的`DoDataExchange`函数中调用此函数，以将字符串属性的值与属性页上的组合框中的当前选择同步。

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
与*pszPropName*指定的控件属性关联的组合框控件的资源 ID。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的组合框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBString` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

在属性页的`DoDataExchange`函数中调用此函数以同步与属性页上组合框中的当前选择完全匹配的字符串属性的值。

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
与*pszPropName*指定的控件属性关联的组合框控件的资源 ID。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的组合框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_CBStringExact` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

在属性页的`DoDataExchange`函数中调用此函数，以将属性的值与关联的属性页复选框控件同步。

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
与*pszPropName*指定的控件属性关联的复选框控件的资源 ID。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*ID*指定的复选框控件交换的控件属性的名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_Check` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

在属性页的`DoDataExchange`函数中调用此函数，以在属性页上的列表框中将整数属性的值与当前选择的索引同步。

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
列表框控件的资源 ID 与*pszPropName*指定的控件属性相关联。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的列表框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBIndex` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

在属性页的`DoDataExchange`函数中调用此函数，以将字符串属性的值与属性页上的列表框中的当前选择同步。

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
列表框控件的资源 ID 与*pszPropName*指定的控件属性相关联。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的列表框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBString` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

在属性页的`DoDataExchange`函数中调用此函数以同步与属性页上列表框中的当前选择完全匹配的字符串属性的值。

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
列表框控件的资源 ID 与*pszPropName*指定的控件属性相关联。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的列表框字符串交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_LBStringExact` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

在属性页的`DoDataExchange`函数中调用此函数，以在保存属性值时完成属性值从属性页传输到控件。

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

### <a name="remarks"></a>备注

完成所有数据交换函数后，应调用此功能。 例如：

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

在控件的`DoPropExchange`函数中调用此函数，以将属性的值与关联的属性页单选按钮控件同步。

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
与*pszPropName*指定的控件属性关联的单选按钮控件的资源 ID。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*ID*指定的单选按钮控件交换的控件属性的名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_Radio` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

在控件的`DoDataExchange`函数中调用此函数以将属性的值与关联的属性页控件同步。

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
与*pszPropName*指定的控件属性关联的控件的资源 ID。

*成员*<br/>
与*id*指定的属性页控件和*pszPropName*指定的属性关联的成员变量。

*pszProp名称*<br/>
要与*id*指定的控件交换的控件属性的属性名称。

### <a name="remarks"></a>备注

应在相应的 `DDX_Text` 函数调用之前调用此函数。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

开始定义控件的属性页页 I。

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>参数

*class_name*<br/>
为其指定属性页的属性类的名称。

*count*<br/>
控件类使用的属性页数。

### <a name="remarks"></a>备注

在定义类成员函数的实现 （.cpp） 文件中，使用BEGIN_PROPPAGEIDS宏启动属性页列表，然后为每个属性页添加宏条目，然后使用END_PROPPAGEIDS宏完成属性页列表。

有关属性页的详细信息，请参阅文章[ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

结束属性页 ID 列表的定义。

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
拥有属性页的控件类的名称。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PropPAGEID

添加属性页供 OLE 控件使用。

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>参数

*Clsid*<br/>
属性页的唯一类 ID。

### <a name="remarks"></a>备注

所有 PROPPAGEID 宏都必须放置在控件的实现文件中的BEGIN_PROPPAGEIDS和END_PROPPAGEIDS宏之间。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
