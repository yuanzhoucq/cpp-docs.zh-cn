---
title: 调度映射
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365757"
---
# <a name="dispatch-maps"></a>调度映射

OLE 自动化提供了调用方法和跨应用程序访问属性的方法。 Microsoft 基础类库提供的用于调度这些请求的机制是"调度映射"，它指定对象函数和属性的内部和外部名称，以及属性本身和函数参数的数据类型。

|调度映射宏|说明|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|声明调度映射将用于公开类的方法和属性（必须在类声明中使用）。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|开始调度映射的定义。|
|[END_DISPATCH_MAP](#end_dispatch_map)|结束调度映射的定义。|
|[DISP_FUNCTION](#disp_function)|在调度映射中用于定义 OLE 自动化功能。|
|[DISP_PROPERTY](#disp_property)|定义 OLE 自动化属性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定义 OLE 自动化属性并命名"获取和设置"函数。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定义带有通知的 OLE 自动化属性。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定义一个 OLE 自动化属性，该属性采用参数并命名"获取"和"设置"函数。|
|[DISP_DEFVALUE](#disp_defvalue)|将现有属性设为对象的默认值。|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

如果程序中`CCmdTarget`的派生类支持 OLE 自动化，则该类必须提供调度映射才能公开其方法和属性。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>备注

在类声明末尾使用DECLARE_DISPATCH_MAP宏。 然后，在 中。定义类成员函数的 CPP 文件，使用BEGIN_DISPATCH_MAP宏。 然后包括每个类公开方法和属性（DISP_FUNCTION、DISP_PROPERTY等）的宏条目。 最后，使用END_DISPATCH_MAP宏。

> [!NOTE]
> 如果在DECLARE_DISPATCH_MAP之后声明任何成员，则必须为其指定新的访问类型（**公共**、**私有**或**受保护**）。

应用程序向导和代码向导可帮助创建自动化类和维护调度映射。 有关调度映射的详细信息，请参阅[自动化服务器](../../mfc/automation-servers.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

声明调度映射的定义。

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定拥有此调度映射的类的名称。

*基类*<br/>
指定*类 的*基类名称。

### <a name="remarks"></a>备注

在定义类成员函数的实现 （.cpp） 文件中，使用BEGIN_DISPATCH_MAP宏启动调度映射，为每个调度函数和属性添加宏条目，以及使用END_DISPATCH_MAP宏完成调度映射。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

结束调度映射的定义。

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>备注

它必须与BEGIN_DISPATCH_MAP一起使用。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

在调度映射中定义 OLE 自动化功能。

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
函数的外部名称。

*pfn成员*<br/>
成员函数的名称。

*弗特雷特瓦尔*<br/>
指定函数返回类型的值。

*vtsParams*<br/>
指定函数参数列表的一个或多个常量的空间分隔列表。

### <a name="remarks"></a>备注

*vtRetVal*参数的类型为 VARTYPE。 此参数的以下可能值取自`VARENUM`枚举：

|符号|返回类型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**长**|
|VT_R4|**浮动**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*vtsParams*参数是空格分隔的值列表和`VTS_*`常量。 一个或多个这些值由空格（不是逗号）分隔，指定函数的参数列表。 例如，

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整数的列表，后跟指向短整数的指针。

常`VTS_`量及其含义如下：

|符号|参数类型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**长**|
|VTS_R4|**浮动**|
|VTS_R8|**double**|
|VTS_CY|`const CY` 或 `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` 或 `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__短\*__|
|VTS_PI4|__长\*__|
|VTS_PR4|__浮动\*__|
|VTS_PR8|__双\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|无参数|

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

在调度映射中定义 OLE 自动化属性。

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*成员名称*<br/>
属性存储在其中的成员变量的名称。

*vtPropType*<br/>
指定属性类型的值。

### <a name="remarks"></a>备注

*vtPropType*参数的类型为**VARTYPE**。 此参数的可能值取自 VARENUM 枚举：

|符号|属性类型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**长**|
|VT_R4|**浮动**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

当外部客户端更改属性时，*成员名称*指定的成员变量的值将更改;没有更改的通知。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

定义 OLE 自动化属性，并在调度映射中命名用于获取和设置该属性值的函数。

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*成员获取*<br/>
用于获取属性的成员函数的名称。

*成员集*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
指定属性类型的值。

### <a name="remarks"></a>备注

*iGet*和*iset*函数具有由*vtPropType*参数确定的签名。 *iget*函数不采用任何参数，并返回*vtPropType*指定的类型的值。 *成员集*函数采用*vtPropType*指定的类型的参数，不返回任何内容。

*vtPropType*参数的类型为 VARTYPE。 此参数的可能值取自 VARENUM 枚举。 有关这些值的列表，请参阅[DISP_FUNCTION](#disp_function)中的*vtRetVal*参数的备注。 请注意，DISP_FUNCTION注释中列出的VT_EMPTY不允许作为属性数据类型。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

在调度映射中定义具有通知的 OLE 自动化属性。

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*sz 外部名称*<br/>
属性的外部名称。

*成员名称*<br/>
属性存储在其中的成员变量的名称。

*pfn 后集*<br/>
*sz外部名称*的通知函数的名称。

*vtPropType*<br/>
指定属性类型的值。

### <a name="remarks"></a>备注

与使用DISP_PROPERTY定义的属性不同，使用DISP_PROPERTY_NOTIFY定义的属性将在更改该属性时自动调用*pfnAfterSet*指定的函数。

*vtPropType*参数的类型为 VARTYPE。 此参数的可能值取自 VARENUM 枚举：

|符号|属性类型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**长**|
|VT_R4|**浮动**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

定义使用单独的`Get`和`Set`成员函数访问的属性。

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*psz外部名称*<br/>
属性的外部名称。

*普芬获取*<br/>
用于获取属性的成员函数的名称。

*pfnSet*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
指定属性类型的值。

*vtsParams*<br/>
空间分隔`VTS_*`变体参数类型的字符串，每个参数一个。

### <a name="remarks"></a>备注

与DISP_PROPERTY_EX宏不同，此宏允许您为属性指定参数列表。 这对于实现索引或参数化的属性非常有用。

### <a name="example"></a>示例

请考虑以下 get 和 set 成员函数的声明，这些函数允许用户在访问属性时请求特定的行和列：

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

这些对应于控制调度映射中的以下DISP_PROPERTY_PARAM宏：

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

作为另一个示例，请考虑以下获取和设置成员函数：

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

这些对应于控制调度映射中的以下DISP_PROPERTY_PARAM宏：

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

将现有属性设为对象的默认值。

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
表示对象的“值”的属性的外部名称。

### <a name="remarks"></a>备注

使用默认值可以为 Visual Basic 应用程序简化对您的自动化对象的编程。

您的对象的“默认值”是在对对象的引用未指定属性或成员函数时检索到或设置的属性。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
