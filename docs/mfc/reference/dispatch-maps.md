---
title: 调度映射
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916516"
---
# <a name="dispatch-maps"></a>调度映射

OLE 自动化提供了调用方法和跨应用程序访问属性的方法。 用于分派这些请求的 Microsoft 基础类库提供的机制是 "调度映射", 用于指定对象函数和属性的内部和外部名称, 以及属性本身和的数据类型函数参数。

|调度映射宏|描述|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|声明调度映射将用于公开类的方法和属性 (必须在类声明中使用)。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|启动调度映射的定义。|
|[END_DISPATCH_MAP](#end_dispatch_map)|结束调度映射的定义。|
|[DISP_FUNCTION](#disp_function)|用于调度映射中, 用于定义 OLE 自动化函数。|
|[DISP_PROPERTY](#disp_property)|定义 OLE 自动化属性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定义 OLE 自动化属性并命名 Get 和 Set 函数。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定义带有通知的 OLE 自动化属性。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定义一个 OLE 自动化属性, 该属性采用参数并命名 Get 和 Set 函数。|
|[DISP_DEFVALUE](#disp_defvalue)|将现有属性设为对象的默认值。|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

如果程序`CCmdTarget`中派生的类支持 OLE 自动化, 则该类必须提供一个调度映射来公开其方法和属性。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>备注

在类声明的末尾使用 DECLARE_DISPATCH_MAP 宏。 然后, 在中。CPP 文件, 用于定义类的成员函数, 请使用 BEGIN_DISPATCH_MAP 宏。 然后, 为类的每个公开的方法和属性 (DISP_FUNCTION、DISP_PROPERTY 等) 添加宏项。 最后, 使用 END_DISPATCH_MAP 宏。

> [!NOTE]
> 如果在 DECLARE_DISPATCH_MAP 后声明任何成员, 则必须为它们指定新的访问类型 (**公共**、**私有**或**受保护**)。

应用程序向导和代码向导有助于创建自动化类和维护调度映射。 有关调度映射的详细信息, 请参阅[自动化服务器](../../mfc/automation-servers.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP

声明调度映射的定义。

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>参数

*theClass*<br/>
指定拥有此调度映射的类的名称。

*baseClass*<br/>
指定*类*的基类名称。

### <a name="remarks"></a>备注

在定义类的成员函数的实现 (.cpp) 文件中, 通过 BEGIN_DISPATCH_MAP 宏启动调度映射, 为每个调度函数和属性添加宏项, 并通过 END_DISPATCH_ 完成调度映射。映射宏。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

结束调度映射的定义。

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>备注

它必须与 BEGIN_DISPATCH_MAP 结合使用。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

定义调度映射中的 OLE 自动化函数。

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>参数

*theClass*<br/>
类的名称。

*pszName*<br/>
函数的外部名称。

*pfnMember*<br/>
成员函数的名称。

*vtRetVal*<br/>
一个值, 该值指定函数的返回类型。

*vtsParams*<br/>
用空格分隔的列表, 其中的一个或多个常量指定函数的参数列表。

### <a name="remarks"></a>备注

*VtRetVal*参数的类型为 VARTYPE。 此参数的以下可能值来自`VARENUM`枚举:

|符号|返回类型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams*参数是`VTS_*`常量的以空格分隔的值列表。 这些值中的一个或多个由空格 (而不是逗号) 分隔) 指定函数的参数列表。 例如，应用于对象的

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整数的列表, 后跟一个指向短整数的指针。

`VTS_`常量及其含义如下:

|符号|参数类型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` 或 `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` 或 `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__漫长\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__double\*__|
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

## <a name="disp_property"></a>DISP_PROPERTY

定义调度映射中的 OLE 自动化属性。

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>参数

*theClass*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*memberName*<br/>
存储属性的成员变量的名称。

*vtPropType*<br/>
一个指定属性类型的值。

### <a name="remarks"></a>备注

*VtPropType*参数的类型为**VARTYPE**。 此参数的可能值取自 VARENUM 枚举:

|符号|属性类型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

当外部客户端更改属性时, 由成员指定的成员变量的值将更改;没有更改通知。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

定义 OLE 自动化属性, 并将用于获取和设置属性值的函数命名为调度映射。

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>参数

*theClass*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*memberGet*<br/>
用于获取属性的成员函数的名称。

*memberSet*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
一个指定属性类型的值。

### <a name="remarks"></a>备注

*MemberGet*和*成员集*函数的签名由*vtPropType*参数决定。 *MemberGet*函数不采用任何参数, 并返回由*vtPropType*指定的类型的值。 *成员集*函数使用由*vtPropType*指定的类型的自变量, 并且不返回任何内容。

*VtPropType*参数的类型为 VARTYPE。 此参数的可能值取自 VARENUM 枚举。 有关这些值的列表, 请参阅[DISP_FUNCTION](#disp_function)中的*vtRetVal*参数备注。 请注意, 在 DISP_FUNCTION 备注中列出的 VT_EMPTY 不允许用作属性数据类型。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

在调度映射中定义带有通知的 OLE 自动化属性。

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>参数

*theClass*<br/>
类的名称。

*szExternalName*<br/>
属性的外部名称。

*memberName*<br/>
存储属性的成员变量的名称。

*pfnAfterSet*<br/>
*SzExternalName*的通知函数的名称。

*vtPropType*<br/>
一个指定属性类型的值。

### <a name="remarks"></a>备注

与使用 DISP_PROPERTY 定义的属性不同, 使用 DISP_PROPERTY_NOTIFY 定义的属性会在属性更改时自动调用*pfnAfterSet*指定的函数。

*VtPropType*参数的类型为 VARTYPE。 此参数的可能值取自 VARENUM 枚举:

|符号|属性类型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
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

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM

定义使用单独`Get`的和`Set`成员函数访问的属性。

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

*theClass*<br/>
类的名称。

*pszExternalName*<br/>
属性的外部名称。

*pfnGet*<br/>
用于获取属性的成员函数的名称。

*pfnSet*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
一个指定属性类型的值。

*vtsParams*<br/>
一串空格分隔`VTS_*`的变量参数类型, 每个参数一个。

### <a name="remarks"></a>备注

与 DISP_PROPERTY_EX 宏不同, 此宏允许您为属性指定参数列表。 这对于实现索引或参数化的属性很有用。

### <a name="example"></a>示例

请考虑以下 get 和 set 成员函数的声明, 这些函数允许用户在访问属性时请求特定行和列:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

它们对应于控件调度映射中的以下 DISP_PROPERTY_PARAM 宏:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

作为另一个示例, 请考虑以下 get 和 set 成员函数:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

它们对应于控件调度映射中的以下 DISP_PROPERTY_PARAM 宏:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

将现有属性设为对象的默认值。

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>参数

*theClass*<br/>
类的名称。

*pszName*<br/>
表示对象的“值”的属性的外部名称。

### <a name="remarks"></a>备注

使用默认值可以为 Visual Basic 应用程序简化对您的自动化对象的编程。

您的对象的“默认值”是在对对象的引用未指定属性或成员函数时检索到或设置的属性。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>请参阅

[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)
