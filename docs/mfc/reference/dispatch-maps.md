---
title: 调度映射 |Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d22c94513e80c4f353de9e10588f219a2d3be92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388064"
---
# <a name="dispatch-maps"></a>调度映射

OLE 自动化提供了方法调用的方法和属性访问跨应用程序。 由 Microsoft 基础类库的调度这些请求提供的机制是"分派映射"，它指定了内部和外部的对象的函数和属性，以及数据类型和属性本身的名称函数自变量。

|调度映射宏|描述|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|声明调度映射将用于公开类的方法和属性 （必须在类声明中使用）。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|启动调度映射的定义。|
|[END_DISPATCH_MAP](#end_dispatch_map)|结束调度映射的定义。|
|[DISP_FUNCTION](#disp_function)|调度映射中使用，以定义 OLE 自动化函数。|
|[DISP_PROPERTY](#disp_property)|定义 OLE 自动化属性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定义了一个 OLE 自动化属性并将 Get 和 Set 函数。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定义 OLE 自动化属性，并发出通知。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定义 Get 和 Set 函数采用参数和名称的 OLE 自动化属性。|
|[DISP_DEFVALUE](#disp_defvalue)|将现有属性设为对象的默认值。|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

如果`CCmdTarget`-在程序中的派生的类支持 OLE 自动化，类必须提供调度映射，以公开其方法和属性。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>备注

在类声明的末尾使用 DECLARE_DISPATCH_MAP 宏。 然后，在。定义类的成员函数 CPP 文件使用 BEGIN_DISPATCH_MAP 宏。 然后为您的类公开的方法和属性 （DISP_FUNCTION、 DISP_PROPERTY，等） 的每个包含宏条目。 最后，使用 END_DISPATCH_MAP 宏。

> [!NOTE]
> 如果之后 DECLARE_DISPATCH_MAP 声明任何成员，则必须指定新的访问类型 (**公共**，**专用**，或**保护**) 为它们。

在创建自动化类并维护调度映射，从而提供协助应用程序向导和代码向导。 调度映射的详细信息，请参阅[自动化服务器](../../mfc/automation-servers.md)。

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

*类*<br/>
指定拥有此调度映射的类的名称。

*baseClass*<br/>
指定的基类名称*类*。

### <a name="remarks"></a>备注

在实现 (.cpp) 文件中定义您的类的成员函数，使用 BEGIN_DISPATCH_MAP 宏启动调度映射、 为每个调度函数和属性，添加宏条目并完成与 END_DISPATCH_ 调度映射映射宏。

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

调度映射中定义的 OLE 自动化函数。

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

*pfnMember*<br/>
成员函数的名称。

*vtRetVal*<br/>
指定函数的返回类型的值。

*vtsParams*<br/>
指定函数的参数列表的一个或多个常量的以空格分隔的列表。

### <a name="remarks"></a>备注

*VtRetVal*参数属于 VARTYPE 类型。 此参数的以下可能值取自`VARENUM`枚举：

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

*VtsParams*参数是以空格分隔的值列表`VTS_*`常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如，应用于对象的

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整型短整数后跟一个指针的列表。

`VTS_`常量和它们的含义如下所示：

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
|VTS_PI4|__长\*__|
|VTS_PR4|__Float\*__|
|VTS_PR8|__双精度\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|没有参数|

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property"></a>  DISP_PROPERTY

调度映射中定义的 OLE 自动化属性。

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
在其中存储属性的成员变量的名称。

*vtPropType*<br/>
一个指定属性的类型值。

### <a name="remarks"></a>备注

*VtPropType*自变量的类型是**VARTYPE**。 为此参数的可能值取自 VARENUM 枚举：

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

当外部客户端更改的属性，指定的成员变量的值*memberName*更改; 更改的通知中不存在。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

用于获取和设置属性的值中调度映射的函数定义 OLE 自动化属性和名称。

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

*memberGet*<br/>
用来获取属性的成员函数的名称。

*成员集*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
一个指定属性的类型值。

### <a name="remarks"></a>备注

*MemberGet*并*memberSet*函数具有签名由*vtPropType*参数。 *MemberGet*函数不采用任何参数，并返回由指定类型的值*vtPropType*。 *MemberSet*函数采用指定的类型的参数*vtPropType*并不返回任何内容。

*VtPropType*参数属于 VARTYPE 类型。 为此参数的可能值取自 VARENUM 枚举。 有关这些值的列表，请参阅备注*vtRetVal*中的参数[DISP_FUNCTION](#disp_function)。 请注意，VT_EMPTY，列出 DISP_FUNCTION 注释中不能作为属性数据类型。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

调度映射中定义具有通知的 OLE 自动化属性。

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

*szExternalName*<br/>
属性的外部名称。

*成员名称*<br/>
在其中存储属性的成员变量的名称。

*pfnAfterSet*<br/>
有关通知函数的名称*szExternalName*。

*vtPropType*<br/>
一个指定属性的类型值。

### <a name="remarks"></a>备注

DISP_PROPERTY 具有定义的属性，与使用 DISP_PROPERTY_NOTIFY 定义的属性将自动调用由指定的函数*pfnAfterSet*时更改的属性。

*VtPropType*参数属于 VARTYPE 类型。 为此参数的可能值取自 VARENUM 枚举：

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

定义具有单独访问的属性`Get`和`Set`成员函数。

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

*pszExternalName*<br/>
属性的外部名称。

*pfnGet*<br/>
用来获取属性的成员函数的名称。

*pfnSet*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
一个指定属性的类型值。

*vtsParams*<br/>
以空格分隔的字符串`VTS_*`变量参数类型，另一个用于每个参数。

### <a name="remarks"></a>备注

与不同 DISP_PROPERTY_EX 宏，此宏，可指定该属性的参数列表。 这可用于实现的索引或参数化属性。

### <a name="example"></a>示例

请考虑以下声明的 get 和 set 函数，允许用户访问该属性时请求特定的行和列的成员：

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

这些会对应于控件调度映射中的以下 DISP_PROPERTY_PARAM 宏：

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

作为另一个示例，请考虑以下 get 和 set 函数的成员：

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

这些会对应于控件调度映射中的以下 DISP_PROPERTY_PARAM 宏：

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

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

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
