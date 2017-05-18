---
title: "CComCurrency 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
dev_langs:
- C++
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 1b0b4fa5f42bd060b08ef90d09eee8d9d2d76fe6
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcurrency-class"></a>CComCurrency 类
`CComCurrency` 具有用于创建和管理 CURRENCY 对象的方法和运算符。  
  
## <a name="syntax"></a>语法  
  
```
class CComCurrency
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|`CComCurrency` 对象的构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|返回 `m_currency` 数据成员的地址。|  
|[CComCurrency::GetFraction](#getfraction)|调用此方法以返回 `CComCurrency` 对象的小数部分。|  
|[CComCurrency::GetInteger](#getinteger)|调用此方法以返回 `CComCurrency` 对象的整数部分。|  
|[CComCurrency::Round](#round)|调用此方法以将 `CComCurrency` 对象舍入为最接近的整数值。|  
|[CComCurrency::SetFraction](#setfraction)|调用此方法以设置 `CComCurrency` 对象的小数部分。|  
|[CComCurrency::SetInteger](#setinteger)|调用此方法以设置 `CComCurrency` 对象的整数部分。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComCurrency::operator-](#operator_-)|此运算符用于对 `CComCurrency` 对象执行减法。|  
|[CComCurrency::operator ！ =](#operator_neq)|比较两个 `CComCurrency` 对象是否相等。|  
|[CComCurrency::operator *](#operator_star)|此运算符用于对 `CComCurrency` 对象执行乘法。|  
|[CComCurrency::operator * =](#operator_star_eq)|此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。|  
|[CComCurrency::operator /](#operator_div)|此运算符用于对 `CComCurrency` 对象执行除法。|  
|[CComCurrency::operator / =](#operator_div_eq)|此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。|  
|[CComCurrency::operator +](#operator_add)|此运算符用于对 `CComCurrency` 对象执行加法。|  
|[CComCurrency::operator + =](#operator_add_eq)|此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。|  
|[CComCurrency::operator](#operator_lt)|此运算符比较两个 `CComCurrency` 对象以确定较小者。|  
|[CComCurrency::operator<>](#operator_lt_eq)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。|  
|[CComCurrency::operator =](#operator_eq)|此运算符向 `CComCurrency` 对象赋予新值。|  
|[CComCurrency::operator =](#operator_-_eq)|此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。|  
|[CComCurrency::operator = =](#operator_eq_eq)|此运算符比较两个 `CComCurrency` 对象是否相等。|  
|[CComCurrency::operator&1;>](#operator_gt)|此运算符比较两个 `CComCurrency` 对象以确定较大者。|  
|[CComCurrency::operator&1;> =](#operator_gt_eq)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。|  
|[CComCurrency::operator 货币](#operator_currency)|强制转换 `CURRENCY` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|由类实例创建的 `CURRENCY` 变量。|  
  
## <a name="remarks"></a>备注  
 `CComCurrency`是包装**货币**数据类型。 **货币**实现为 8 字节 2 的补数整数值乘以 10000。 这产生了一个定点数数字，小数点左侧有 15 位数，右侧有 4 位数。 **货币**数据类型是非常有用，对于涉及资金，计算或任何定点计算准确性至关重要。  
  
 **CComCurrency**包装实现此定点类型算术运算符、 赋值和比较操作。 已选中受支持的应用程序，以控制定点计算过程中可能出现的舍入误差。  
  
 `CComCurrency` 对象以两个组件的形式提供对小数点两侧的数字的访问权限：一个整数组件，它存储小数点左侧的值；一个小数组件，它存储小数点右侧的值。 小数部分在内部存储为-9999 之间的整数值 ( **CY_MIN_FRACTION**) 和 +9999 ( **CY_MAX_FRACTION**)。 该方法[CComCurrency::GetFraction](#getfraction)返回按 10000 的因子进行缩放的值 ( **CY_SCALE**)。  
  
 指定的整数和小数部分组件时**CComCurrency**对象时，请记住的小数部分是范围 0 到 9999 的数字。 在处理美元等在小数点后仅采用两个有效位数来表示金额的货币时，这一点非常有用。 即使不显示最后两位数字，也必须将它们考虑在内。  
  
|值|可能的 CComCurrency 赋值|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency(10,5000)*或*CComCurrency(10.50)|  
|$10.05|CComCurrency(10,500)*或*CComCurrency(10.05)|  
  
 值**CY_MIN_FRACTION**， **CY_MAX_FRACTION**，和**CY_SCALE** atlcur.h 中定义。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcur.h  
  
##  <a name="ccomcurrency"></a>CComCurrency::CComCurrency  
 构造函数。  
  
```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);  
CComCurrency(USHORT usSrc);  
CComCurrency(CHAR cSrc);  
CComCurrency(DOUBLE dSrc);  
CComCurrency(FLOAT fSrc);  
CComCurrency(LONG lSrc);  
CComCurrency(SHORT sSrc);  
CComCurrency(BYTE bSrc);  
CComCurrency(LONGLONG nInteger, SHORT nFraction);  
explicit CComCurrency(LPDISPATCH pDispSrc);  
explicit CComCurrency(const VARIANT& varSrc);  
explicit CComCurrency(LPCWSTR szSrc);  
explicit CComCurrency(LPCSTR szSrc);
```  
  
### <a name="parameters"></a>参数  
 `curSrc`  
 一个现有的 `CComCurrency` 对象。  
  
 `cySrc`  
 类型的变量**货币**。  
  
 `bSrc`, `dSrc`, `fSrc`, `lSrc`, *sSrc*, *ulSrc, usSrc*  
 提供给成员变量的初始值`m_currency`。  
  
 `cSrc`  
 字符，其中包含提供给成员变量的初始值`m_currency`。  
  
 `nInteger`*nFraction*  
 整数和小数部分的初始货币值。 请参阅[CComCurrency](../../atl/reference/ccomcurrency-class.md)的详细信息的概述。  
  
 `pDispSrc`  
 `IDispatch`指针。  
  
 *varSrc*  
 类型的变量**VARIANT**。 使用当前线程的区域设置来执行转换。  
  
 `szSrc`  
 包含的初始值的 Unicode 或 ANSI 字符串。 使用当前线程的区域设置来执行转换。  
  
### <a name="remarks"></a>备注  
 该构造函数设置初始值[CComCurrency::m_currency](#m_currency)，并接受的数据类型，包括整数、 字符串、 浮点数，范围广泛**货币**变量和其他`CComCurrency`对象。 如果未提供值，`m_currency`设置为 0。  
  
 如果出现错误，如溢出，缺少空异常规范的构造函数 ( **throw （)**) 调用`AtlThrow`与描述该错误的 HRESULT。  
  
 当使用浮点或双精度值分配一个值，请注意， **CComCurrency(10.50)**等同于**CComCurrency(10,5000)**和 not **CComCurrency(10,50)**。  
  
##  <a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr  
 返回 `m_currency` 数据成员的地址。  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的地址`m_currency`数据成员  
  
##  <a name="getfraction"></a>CComCurrency::GetFraction  
 调用此方法可返回的小数部分`CComCurrency`对象。  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的小数部分`m_currency`数据成员。  
  
### <a name="remarks"></a>备注  
 小数部分是-9999 之间的 4 位数字的整数值 ( **CY_MIN_FRACTION**) 和 +9999 ( **CY_MAX_FRACTION**)。 `GetFraction`返回的 10000 此值 ( **CY_SCALE**)。 值**CY_MIN_FRACTION**， **CY_MAX_FRACTION**，和**CY_SCALE** atlcur.h 中定义。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&50;](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>CComCurrency::GetInteger  
 调用此方法以获取的整数部分`CComCurrency`对象。  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的整数部分`m_currency`数据成员。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&51;](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>CComCurrency::m_currency  
 **货币**数据成员。  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>备注  
 此成员将具有访问和操作的此类方法的货币。  
  
##  <a name="operator_-"></a>CComCurrency::operator-  
 此运算符用于对 `CComCurrency` 对象执行减法。  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示该减法运算的结果。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&55;](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>CComCurrency::operator ！ =  
 此运算符比较两个对象不相等。  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 要比较的 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**要比较的项是否不等于`CComCurrency`对象; 否则为**false**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&56;](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>CComCurrency::operator *  
 此运算符用于对 `CComCurrency` 对象执行乘法。  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `nOperand`  
 乘数。  
  
 `cur`  
 `CComCurrency`用作乘数对象。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示乘法运算的结果。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&57;](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>CComCurrency::operator * =  
 此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>参数  
 `nOperand`  
 乘数。  
  
 `cur`  
 `CComCurrency`用作乘数对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&58; 页](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>CComCurrency::operator /  
 此运算符用于对 `CComCurrency` 对象执行除法。  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>参数  
 `nOperand`  
 除数。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`表示除法运算结果的对象。 如果除数为零，则会出现断言失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&59;](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>CComCurrency::operator / =  
 此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>参数  
 `nOperand`  
 除数。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果除数为零，则会出现断言失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&60;](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>CComCurrency::operator +  
 此运算符用于对 `CComCurrency` 对象执行加法。  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 `CComCurrency`对象添加到原始对象。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示加法结果。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&61;](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>CComCurrency::operator + =  
 此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&62;](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>CComCurrency::operator&lt;  
 此运算符比较两个 `CComCurrency` 对象以确定较小者。  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否小于第二个**false**否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&63;](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>CComCurrency::operator&lt;=  
 此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否小于或等于第二个**false**否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&64;](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>CComCurrency::operator =  
 此运算符向 `CComCurrency` 对象赋予新值。  
  
```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```  
  
### <a name="parameters"></a>参数  
 `curSrc`  
 一个**CComCurrency**对象。  
  
 `cySrc`  
 类型的变量**货币**。  
  
 *sSrc*, `fSrc`, `lSrc`, *bSrc*, *usSrc*, `dSrc`, *cSrc*, *ulSrc*,`dSrc`  
 数值将分配给`CComCurrency`对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&65;](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>CComCurrency::operator =  
 此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，如溢出，此运算符调用`AtlThrow`与描述该错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&66;](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>CComCurrency::operator = =  
 此运算符比较两个 `CComCurrency` 对象是否相等。  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 `CComCurrency`对象进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果对象相等 (即，`m_currency`数据成员，则这两个整数和小数部分组成，在这两对象具有相同的值)， **false**否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&67;](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>CComCurrency::operator&gt;  
 此运算符比较两个 `CComCurrency` 对象以确定较大者。  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否大于第二个**false**否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&68;](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>CComCurrency::operator&gt;=  
 此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 `cur`  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否大于或等于第二个**false**否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&69;](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>CComCurrency::operator 货币  
 这些运算符用于强制转换`CComCurrency`对象传递给**货币**数据类型。  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回对**货币**对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&70;](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>CComCurrency::Round  
 调用此方法要舍入到指定的小数位数的货币。  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>参数  
 *nDecimals*  
 向其数字个数`m_currency`将舍入，在 0 到 4 范围内。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&52;](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>CComCurrency::SetFraction  
 调用此方法以设置 `CComCurrency` 对象的小数部分。  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>参数  
 *nFraction*  
 要分配到的小数部分的值`m_currency`数据成员。 符号的小数部分必须与整数部分中，相同和的值必须是-9999 范围内 ( **CY_MIN_FRACTION**) 到 +9999 ( **CY_MAX_FRACTION**)。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&53;](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>CComCurrency::SetInteger  
 调用此方法以设置 `CComCurrency` 对象的整数部分。  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>参数  
 `nInteger`  
 要分配给的整数部分的值`m_currency`数据成员。 符号的整数部分必须匹配现有的小数部分的符号。  
  
 `nInteger`必须在范围内**CY_MIN_INTEGER**到**CY_MAX_INTEGER** （含)。 Atlcur.h 中定义这些值。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&54;](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [COleCurrency 类](../../mfc/reference/colecurrency-class.md)   
 [货币](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [类概述](../../atl/atl-class-overview.md)

