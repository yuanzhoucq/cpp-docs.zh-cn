---
title: 调度映射 |Microsoft 文档
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
ms.openlocfilehash: 107dba503c11d3810f75dcd4ee6e6f5af47008fc
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122975"
---
# <a name="dispatch-maps"></a>调度映射

OLE 自动化提供方法来调用方法和跨应用程序中访问属性。 由 Microsoft 基础类库用于调度这些请求提供的机制是"调度映射"，它指定了对象函数和属性，以及属性本身的和的数据类型的内部和外部名称函数自变量。

|调度映射宏|描述|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|声明调度映射将用于公开的类的方法和属性 （必须在类声明中使用）。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|启动调度映射的定义。|
|[END_DISPATCH_MAP](#end_dispatch_map)|结束调度映射的定义。|
|[DISP_FUNCTION](#disp_function)|调度映射中用于定义 OLE 自动化函数。|
|[DISP_PROPERTY](#disp_property)|定义 OLE 自动化属性。|
|[DISP_PROPERTY_EX](#disp_property_ex)|定义 OLE 自动化属性和名称的 Get 和 Set 函数。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定义通知的 OLE 自动化的属性。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|定义 OLE 自动化属性，它采用参数和名称的 Get 和 Set 函数。|
|[DISP_DEFVALUE](#disp_defvalue)|将现有属性设为对象的默认值。|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

如果`CCmdTarget`-你的程序中的派生的类支持 OLE 自动化，类必须提供一个调度映射来公开其方法和属性。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>备注

在类声明的末尾使用 DECLARE_DISPATCH_MAP 宏。 然后，在。定义为类的成员函数的 CPP 文件使用 BEGIN_DISPATCH_MAP 宏。 然后为每个类的公开的方法和属性 （DISP_FUNCTION、 DISP_PROPERTY，依次类推） 包括宏条目。 最后，使用 END_DISPATCH_MAP 宏。

> [!NOTE]
> 如果之后 DECLARE_DISPATCH_MAP 声明任何成员，则必须指定新的访问类型 (**公共**，**私有**，或**保护**) 为它们。

应用程序向导和代码向导帮助创建自动化类并维护调度映射可帮助。 调度映射的详细信息，请参阅[自动化服务器](../../mfc/automation-servers.md)。

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

*类*  
指定拥有此调度映射的类的名称。

*baseClass*  
指定的基类名称*类*。

### <a name="remarks"></a>备注

在实现 (.cpp) 文件中定义你的类的成员函数，用 BEGIN_DISPATCH_MAP 宏启动调度映射，为每个调度函数和属性，添加宏条目并完成用 END_DISPATCH_ 调度映射映射宏。

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

调度映射中定义 OLE 自动化函数。

```cpp
DISP_FUNCTION(
  theClass,
  pszName,
  pfnMember,
  vtRetVal,
  vtsParams)
```

### <a name="parameters"></a>参数

*类*  
类的名称。

*pszName*  
函数的外部名称。

*pfnMember*  
成员函数的名称。

*vtRetVal*  
指定函数的返回类型的值。

*vtsParams*  
指定函数的参数列表的一个或多个常量的以空格分隔的列表。

### <a name="remarks"></a>备注

*VtRetVal*自变量为类型 VARTYPE。 以下可能值为此参数，将从`VARENUM`枚举：

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

*VtsParams*自变量是空格分隔的值从列表`VTS_*`常量。 一个或多个用空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如，应用于对象的

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

指定包含短整数跟短整数的指针的列表。

`VTS_`常量和它们的含义如下：

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
|VTS_PR4|__float\*__|
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

调度映射中定义 OLE 自动化属性。

```cpp
DISP_PROPERTY(
  theClass,
  pszName,
  memberName,
  vtPropType)
```

### <a name="parameters"></a>参数

*类*  
类的名称。

*pszName*  
属性的外部名称。

*成员名称*  
在其中存储属性的成员变量的名称。

*vtPropType*  
指定属性的类型的值。

### <a name="remarks"></a>备注

*VtPropType*自变量为类型**VARTYPE**。 为此参数的可能值取自 VARENUM 枚举：

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

外部客户端更改的属性，指定的成员变量的值时*memberName*更改; 则不显示通知的更改。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

定义 OLE 自动化属性和名称用获取和设置调度映射中的属性的值的函数。

```cpp
DISP_PROPERTY_EX(
  theClass,
  pszName,
  memberGet,
  memberSet,
  vtPropType)
```

### <a name="parameters"></a>参数

*类*  
类的名称。

*pszName*  
属性的外部名称。

*memberGet*  
用来获取属性的成员函数的名称。

*成员集*  
用于设置属性的成员函数的名称。

*vtPropType*  
指定属性的类型的值。

### <a name="remarks"></a>备注

*MemberGet*和*memberSet*函数具有由签名*vtPropType*自变量。 *MemberGet*函数不采用任何参数，且返回由指定的类型值*vtPropType*。 *MemberSet*函数采用由指定的类型的自变量*vtPropType*并返回执行任何操作。

*VtPropType*自变量为类型 VARTYPE。 为此参数的可能值取自 VARENUM 枚举。 有关这些值的列表，请参阅备注*vtRetVal*中的参数[DISP_FUNCTION](#disp_function)。 请注意，VT_EMPTY，列出 DISP_FUNCTION 注释中不允许为属性数据类型。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

调度映射中定义通知的 OLE 自动化的属性。

```cpp
DISP_PROPERTY_NOTIFY(
  theClass,
  szExternalName,
  memberName,
  pfnAfterSet,
  vtPropType)
```

### <a name="parameters"></a>参数

*类*  
类的名称。

*szExternalName*  
属性的外部名称。

*成员名称*  
在其中存储属性的成员变量的名称。

*pfnAfterSet*  
名称的通知函数*szExternalName*。

*vtPropType*  
指定属性的类型的值。

### <a name="remarks"></a>备注

与使用 DISP_PROPERTY 定义的属性，不同 DISP_PROPERTY_NOTIFY 与定义的属性将自动调用指定函数的*pfnAfterSet*时更改的属性。

*VtPropType*自变量为类型 VARTYPE。 为此参数的可能值取自 VARENUM 枚举：

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

*类*  
类的名称。

*pszExternalName*  
属性的外部名称。

*pfnGet*  
用来获取属性的成员函数的名称。

*pfnSet*  
用于设置属性的成员函数的名称。

*vtPropType*  
指定属性的类型的值。

*vtsParams*  
以空格分隔的字符串`VTS_*`变量参数类型，另一个用于每个参数。

### <a name="remarks"></a>备注

与不同 DISP_PROPERTY_EX 宏，此宏，可指定参数列表的属性。 这可用于实现索引或参数化的属性。

### <a name="example"></a>示例

请考虑以下声明的 get 和 set 允许用户访问该属性时请求的特定行和列的函数的成员：

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

这些方法对应于控件调度映射中的以下 DISP_PROPERTY_PARAM 宏：

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

再举一例，请考虑以下 get 和 set 成员函数：

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

这些方法对应于控件调度映射中的以下 DISP_PROPERTY_PARAM 宏：

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

将现有属性设为对象的默认值。

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>参数

*类*  
类的名称。

*pszName*  
表示对象的“值”的属性的外部名称。

### <a name="remarks"></a>备注

使用默认值可以为 Visual Basic 应用程序简化对您的自动化对象的编程。

您的对象的“默认值”是在对对象的引用未指定属性或成员函数时检索到或设置的属性。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)  
