---
title: "调度映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps. macros
- dispatch maps
- dispatch map macros
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 48e5d1fe207089733caa5ed9e8ca30c2de21f95f
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="dispatch-maps"></a>调度映射
OLE 自动化提供了方法调用的方法和跨应用程序访问属性。 由 Microsoft 基础类库用于调度这些请求提供的机制是"分派映射"，它指定了对象函数和属性，以及本身的属性和函数参数的数据类型的内部和外部名称。  
  
### <a name="dispatch-maps"></a>调度映射  
  
|||  
|-|-|  
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|声明调度映射将用于公开类的方法和属性 （必须在类声明中使用）。|  
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|启动调度映射的定义。|  
|[END_DISPATCH_MAP](#end_dispatch_map)|结束调度映射的定义。|  
|[DISP_FUNCTION](#disp_function)|调度映射中使用，以定义 OLE 自动化函数。|  
|[DISP_PROPERTY](#disp_property)|定义 OLE 自动化属性。|  
|[DISP_PROPERTY_EX](#disp_property_ex)|定义 OLE 自动化属性并命名 Get 和 Set 函数。|  
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|定义 OLE 自动化属性并发出通知。|  
|[DISP_PROPERTY_PARAM](#disp_property_param)|定义 OLE 自动化属性的 Get 和 Set 函数采用参数和名称。|  
|[DISP_DEFVALUE](#disp_defvalue)|将现有属性设为对象的默认值。|  
  
##  <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP  
 如果`CCmdTarget`的派生的类在程序中支持 OLE 自动化，类必须提供调度映射，以公开其方法和属性。  
  
```   
DECLARE_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_DISPATCH_MAP`宏在类声明的末尾。 然后，在。为类函数定义的成员的 CPP 文件，请使用`BEGIN_DISPATCH_MAP`宏。 然后将包含宏项，每个类的公开方法和属性 ( `DISP_FUNCTION`， `DISP_PROPERTY`，依此类推)。 最后，使用`END_DISPATCH_MAP`宏。  
  
> [!NOTE]
>  如果声明之后的任何成员`DECLARE_DISPATCH_MAP`，必须指定新的访问类型 (**公共**， `private`，或`protected`) 为它们。  
  
 应用程序向导和代码向导帮助和维护调度映射中创建自动化的类。 调度映射的详细信息，请参阅[自动化服务器](../../mfc/automation-servers.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation #&10;](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]  

### <a name="requirements"></a>要求  
 **标头:** afxwin.h  

##  <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP  
 声明调度映射的定义。  
  
```  
BEGIN_DISPATCH_MAP(theClass, baseClass)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定拥有此调度映射的类的名称。  
  
 `baseClass`  
 指定 `theClass` 的基类名。  
  
### <a name="remarks"></a>备注  
 在定义类的成员函数的实现 (.cpp) 文件中，使用 `BEGIN_DISPATCH_MAP` 宏启动调度映射，为每个调度函数和属性添加宏项，然后使用 `END_DISPATCH_MAP` 宏完成调度映射。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h  

##  <a name="end_dispatch_map"></a>END_DISPATCH_MAP  
 结束调度映射的定义。  
  
```   
END_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>备注  
 它必须与 `BEGIN_DISPATCH_MAP` 一起使用。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h  

##  <a name="disp_function"></a>DISP_FUNCTION  
 定义 OLE 自动化函数中的调度映射。  
  
```   
DISP_FUNCTION(
  theClass, 
  pszName, 
  pfnMember, 
  vtRetVal, 
  vtsParams)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 该函数的外部名称。  
  
 `pfnMember`  
 成员函数的名称。  
  
 `vtRetVal`  
 指定函数的返回类型的值。  
  
 `vtsParams`  
 以空格分隔的指定函数的参数列表的一个或多个常量的列表。  
  
### <a name="remarks"></a>备注  
 `vtRetVal`参数属于类型**VARTYPE**。 此参数的以下可能值取自`VARENUM`枚举︰  
  
|符号|返回类型|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**双精度**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT 类型的值**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `vtsParams`参数是以空格分隔的值列表**VTS_**常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如， 
  
 [!code-cpp[NVC_MFCAutomation #&14;](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]  
  
 指定包含短整型跟短整型指针的列表。  
  
 **VTS_**常量和它们的含义如下︰  
  
|符号|参数类型|  
|------------|--------------------|  
|**VTS_I2**|`Short`|  
|**VTS_I4**|`Long`|  
|**VTS_R4**|**Float**|  
|**VTS_R8**|`Double`|  
|**VTS_CY**|**const CY**或**CY\***|  
|**VTS_DATE**|**日期**|  
|**VTS_BSTR**|`LPCSTR`|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**BOOL**|  
|**VTS_VARIANT**|**const 变体\***或**VARIANT.**|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_PI2**|**短\***|  
|**VTS_PI4**|**长时间\***|  
|**VTS_PR4**|**float\***|  
|**VTS_PR8**|**双精度\***|  
|**VTS_PCY**|**CY\***|  
|**VTS_PDATE**|**日期\***|  
|**VTS_PBSTR**|**BSTR\***|  
|**VTS_PDISPATCH**|**LPDISPATCH\***|  
|**VTS_PSCODE**|**SCODE\***|  
|**VTS_PBOOL**|**BOOL\***|  
|**VTS_PVARIANT**|**VARIANT 类型的值\***|  
|**VTS_PUNKNOWN**|**LPUNKNOWN\***|  
|**VTS_NONE**|没有参数|  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h 

##  <a name="disp_property"></a>DISP_PROPERTY  
 定义 OLE 自动化属性中的调度映射。  
  
```   
DISP_PROPERTY(
  theClass, 
  pszName, 
  memberName, 
  vtPropType)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 该属性的外部名称。  
  
 `memberName`  
 在其中存储该属性的成员变量的名称。  
  
 `vtPropType`  
 指定属性的类型的值。  
  
### <a name="remarks"></a>备注  
 `vtPropType`参数属于类型**VARTYPE**。 为此参数的可能值取自`VARENUM`枚举︰  
  
|符号|**属性类型**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**双精度**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT 类型的值**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 当外部客户端更改的属性，指定的成员变量的值`memberName`更改; 不没有更改任何通知。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h 

##  <a name="disp_property_ex"></a>DISP_PROPERTY_EX  
 用于获取和设置属性的值中的调度映射的函数定义 OLE 自动化属性和名称。  
  
```   
DISP_PROPERTY_EX(
  theClass, 
  pszName, 
  memberGet, 
  memberSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 该属性的外部名称。  
  
 `memberGet`  
 用来获取属性的成员函数的名称。  
  
 `memberSet`  
 用于设置属性的成员函数的名称。  
  
 `vtPropType`  
 指定属性的类型的值。  
  
### <a name="remarks"></a>备注  
 `memberGet`和`memberSet`函数具有签名由`vtPropType`参数。 `memberGet`函数不采用任何参数，并返回一个值所指定的类型`vtPropType`。 `memberSet`函数采用指定的类型的参数`vtPropType`并不返回任何内容。  
  
 `vtPropType`参数属于类型**VARTYPE**。 为此参数的可能值取自`VARENUM`枚举。 有关这些值的列表，请参阅的备注`vtRetVal`中的参数[DISP_FUNCTION](#disp_function)。 请注意， `VT_EMPTY`、 在中列出`DISP_FUNCTION`remarks、 不允许作为属性数据类型。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h 

##  <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY  
 调度映射中定义 OLE 自动化属性并发出通知。  
  
```   
DISP_PROPERTY_NOTIFY(
  theClass, 
  szExternalName, 
  memberName, 
  pfnAfterSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `szExternalName`  
 该属性的外部名称。  
  
 `memberName`  
 在其中存储该属性的成员变量的名称。  
  
 `pfnAfterSet`  
 通知函数的名称`szExternalName`。  
  
 `vtPropType`  
 指定属性的类型的值。  
  
### <a name="remarks"></a>备注  
 与属性定义与不同`DISP_PROPERTY`，与定义的属性`DISP_PROPERTY_NOTIFY`将自动调用由指定的函数`pfnAfterSet`时更改的属性。  
  
 `vtPropType`参数属于类型**VARTYPE**。 为此参数的可能值取自`VARENUM`枚举︰  
  
|符号|**属性类型**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**双精度**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT 类型的值**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h 

##  <a name="disp_property_param"></a>DISP_PROPERTY_PARAM  
 使用单独的访问将属性定义**获取**和`Set`成员函数。  
  
```   
DISP_PROPERTY_PARAM(
  theClass, 
  pszExternalName, 
  pfnGet, 
  pfnSet, 
  vtPropType,
  vtsParams)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 *pszExternalName*  
 该属性的外部名称。  
  
 `pfnGet`  
 用来获取属性的成员函数的名称。  
  
 `pfnSet`  
 用于设置属性的成员函数的名称。  
  
 `vtPropType`  
 指定属性的类型的值。  
  
 `vtsParams`  
 以空格分隔的字符串**VTS_**变量参数类型，另一个用于每个参数。  
  
### <a name="remarks"></a>备注  
 与不同`DISP_PROPERTY_EX`宏，此宏，可指定该属性的参数列表。 这可用于实现索引或参数化的属性。  
  
### <a name="example"></a>示例  
 请考虑以下声明的 get 和 set 允许用户访问该属性时请求特定的行和列的函数的成员︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&9;](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]  
  
 这些方法对应于以下`DISP_PROPERTY_PARAM`中控件调度映射宏︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&10;](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]  
  
 再举一例，请考虑以下 get 和 set 成员函数︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&11;](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]  
  
 这些方法对应于以下`DISP_PROPERTY_PARAM`中控件调度映射宏︰  
  
 [!code-cpp[NVC_MFCActiveXControl #&12;](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h 

##  <a name="disp_defvalue"></a>DISP_DEFVALUE  
 将现有属性设为对象的默认值。  
  
```   
DISP_DEFVALUE(theClass, pszName)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 表示对象的“值”的属性的外部名称。  
  
### <a name="remarks"></a>备注  
 使用默认值可以为 Visual Basic 应用程序简化对您的自动化对象的编程。  
  
 您的对象的“默认值”是在对对象的引用未指定属性或成员函数时检索到或设置的属性。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h 

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

