---
title: CComCurrency 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d3d845f51f59e6072bd0425f34c63e0049dd31
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202532"
---
# <a name="ccomcurrency-class"></a>CComCurrency 类
`CComCurrency` 具有用于创建和管理 CURRENCY 对象的方法和运算符。  
  
## <a name="syntax"></a>语法  
  
```
class CComCurrency
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
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
|[Ccomcurrency:: Operator-](#operator_-)|此运算符用于对 `CComCurrency` 对象执行减法。|  
|[Ccomcurrency:: Operator ！ =](#operator_neq)|比较两个 `CComCurrency` 对象是否相等。|  
|[Ccomcurrency:: Operator *](#operator_star)|此运算符用于对 `CComCurrency` 对象执行乘法。|  
|[Ccomcurrency:: Operator * =](#operator_star_eq)|此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。|  
|[Ccomcurrency:: Operator /](#operator_div)|此运算符用于对 `CComCurrency` 对象执行除法。|  
|[Ccomcurrency:: Operator / =](#operator_div_eq)|此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。|  
|[Ccomcurrency:: Operator +](#operator_add)|此运算符用于对 `CComCurrency` 对象执行加法。|  
|[Ccomcurrency:: Operator + =](#operator_add_eq)|此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。|  
|[Ccomcurrency:: Operator <](#operator_lt)|此运算符比较两个 `CComCurrency` 对象以确定较小者。|  
|[Ccomcurrency:: Operator < =](#operator_lt_eq)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。|  
|[Ccomcurrency:: Operator =](#operator_eq)|此运算符向 `CComCurrency` 对象赋予新值。|  
|[Ccomcurrency:: Operator =](#operator_-_eq)|此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。|  
|[Ccomcurrency:: Operator = =](#operator_eq_eq)|此运算符比较两个 `CComCurrency` 对象是否相等。|  
|[Ccomcurrency:: Operator >](#operator_gt)|此运算符比较两个 `CComCurrency` 对象以确定较大者。|  
|[Ccomcurrency:: Operator > =](#operator_gt_eq)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。|  
|[Ccomcurrency:: Operator 货币](#operator_currency)|将转换为货币对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|创建类实例的货币变量。|  
  
## <a name="remarks"></a>备注  
 `CComCurrency` 是的货币数据类型的包装。 货币作为按 10,000 缩放的 8 字节补码整数值。 这产生了一个定点数数字，小数点左侧有 15 位数，右侧有 4 位数。 货币数据类型为计算涉及到货币或所有定点数计算非常有用精确度至关重要。  
  
 `CComCurrency`包装实现此定点类型的算术、 赋值和比较操作。 已选中受支持的应用程序，以控制定点计算过程中可能出现的舍入误差。  
  
 `CComCurrency` 对象以两个组件的形式提供对小数点两侧的数字的访问权限：一个整数组件，它存储小数点左侧的值；一个小数组件，它存储小数点右侧的值。 小数部分在内部存储为一个介于-9999 (CY_MIN_FRACTION) 和 + 9999 (CY_MAX_FRACTION) 之间的整数值。 该方法[CComCurrency::GetFraction](#getfraction)返回一个按 10000 (CY_SCALE) 进行缩放的值。  
  
 指定整数和小数部分时`CComCurrency`对象，请记住小数部分是 0 到 9999 范围内的数字。 在处理美元等在小数点后仅采用两个有效位数来表示金额的货币时，这一点非常有用。 即使不显示最后两位数字，也必须将它们考虑在内。  
  
|“值”|可能的 CComCurrency 赋值|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency(10,5000)*或*CComCurrency(10.50)|  
|$10.05|CComCurrency(10,500)*或*CComCurrency(10.05)|  
  
 值 CY_MIN_FRACTION、 CY_MAX_FRACTION 和 CY_SCALE atlcur.h 中定义。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcur.h  
  
##  <a name="ccomcurrency"></a>  CComCurrency::CComCurrency  
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
 *curSrc*  
 一个现有的 `CComCurrency` 对象。  
  
 *cySrc*  
 货币类型的变量。  
  
 *bSrc*， *dSrc*， *fSrc*， *lSrc*， *sSrc*， *ulSrc，usSrc*  
 提供给成员变量的初始值`m_currency`。  
  
 *cSrc*  
 字符，其中包含提供给成员变量的初始值`m_currency`。  
  
 *nInteger*， *nFraction*  
 整数和小数部分的初始货币值。 请参阅[CComCurrency](../../atl/reference/ccomcurrency-class.md)的详细信息的概述。  
  
 *pDispSrc*  
 `IDispatch`指针。  
  
 *varSrc*  
 类型的变量的变体。 使用当前线程的区域设置来执行此转换。  
  
 *szSrc*  
 包含初始值的 Unicode 或 ANSI 字符串。 使用当前线程的区域设置来执行此转换。  
  
### <a name="remarks"></a>备注  
 构造函数设置初始值[CComCurrency::m_currency](#m_currency)，并接受数据类型，包括整数、 字符串、 浮点数、 货币变量和其他各种`CComCurrency`对象。 如果未不提供任何值，`m_currency`设置为 0。  
  
 如果出现错误，例如溢出时，缺少空异常规范的构造函数 (**throw （)**) 调用`AtlThrow`使用描述错误的 HRESULT。  
  
 当使用浮点或双精度值将分配一个值，请注意`CComCurrency(10.50)`等效于`CComCurrency(10,5000)`而不`CComCurrency(10,50)`。  
  
##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr  
 返回 `m_currency` 数据成员的地址。  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的地址`m_currency`数据成员  
  
##  <a name="getfraction"></a>  CComCurrency::GetFraction  
 调用此方法返回的小数部分`CComCurrency`对象。  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的小数部分`m_currency`数据成员。  
  
### <a name="remarks"></a>备注  
 小数部分是-9999 (CY_MIN_FRACTION) 和 + 9999 (CY_MAX_FRACTION) 之间的 4 位数字的整数值。 `GetFraction` 返回此值按 10000 (CY_SCALE) 进行缩放。 CY_MIN_FRACTION、 CY_MAX_FRACTION 和 CY_SCALE 的值在 atlcur.h 中定义。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>  CComCurrency::GetInteger  
 调用此方法以获取的整数部分`CComCurrency`对象。  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的整数部分`m_currency`数据成员。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>  CComCurrency::m_currency  
 货币数据成员。  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>备注  
 此成员保留访问和操作的此类方法的货币。  
  
##  <a name="operator_-"></a>  Ccomcurrency:: Operator-  
 此运算符用于对 `CComCurrency` 对象执行减法。  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示该减法运算的结果。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>  Ccomcurrency:: Operator ！ =  
 此运算符比较两个对象不相等。  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 要比较的 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 如果要比较的项不相等，则返回 TRUE`CComCurrency`对象; 否则为 FALSE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>  Ccomcurrency:: Operator *  
 此运算符用于对 `CComCurrency` 对象执行乘法。  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *nOperand*  
 乘数。  
  
 *cur*  
 `CComCurrency`用作乘数对象。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示该乘法运算的结果。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>  Ccomcurrency:: Operator \*=  
 此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>参数  
 *nOperand*  
 乘数。  
  
 *cur*  
 `CComCurrency`用作乘数对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>  Ccomcurrency:: Operator /  
 此运算符用于对 `CComCurrency` 对象执行除法。  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>参数  
 *nOperand*  
 除数。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示该除法运算的结果。 如果除数为 0，将发生了断言失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>  Ccomcurrency:: Operator / =  
 此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>参数  
 *nOperand*  
 除数。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果除数为 0，将发生了断言失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>  Ccomcurrency:: Operator +  
 此运算符用于对 `CComCurrency` 对象执行加法。  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 `CComCurrency`对象添加到原始对象。  
  
### <a name="return-value"></a>返回值  
 返回`CComCurrency`对象，表示加法结果。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>  Ccomcurrency:: Operator + =  
 此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>  Ccomcurrency:: Operator &lt;  
 此运算符比较两个 `CComCurrency` 对象以确定较小者。  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回 TRUE 的第一个对象是否小于第二个，FALSE 否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>  Ccomcurrency:: Operator &lt;=  
 此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 如果第一个对象小于或等于第二个，FALSE 否则，返回 TRUE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>  Ccomcurrency:: Operator =  
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
 *curSrc*  
 一个 `CComCurrency` 对象。  
  
 *cySrc*  
 货币类型的变量。  
  
 *sSrc*， *fSrc*， *lSrc*， *bSrc*， *usSrc*， *dSrc*， *cSrc*， *ulSrc*， *dSrc*  
 要分配到的数字值`CComCurrency`对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>  Ccomcurrency:: Operator =  
 此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComCurrency`对象。 如果出现错误，例如溢出时，此运算符会调用`AtlThrow`使用描述错误的 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>  Ccomcurrency:: Operator = =  
 此运算符比较两个 `CComCurrency` 对象是否相等。  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 `CComCurrency`要比较的对象。  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则返回 TRUE (也就是说，`m_currency`数据成员，则这两个整数和小数部分组成，在这种对象具有相同的值)，则返回 FALSE 否则为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>  Ccomcurrency:: Operator &gt;  
 此运算符比较两个 `CComCurrency` 对象以确定较大者。  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 如果第一个对象不大于第二个为 FALSE，则返回 TRUE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>  Ccomcurrency:: Operator &gt;=  
 此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>参数  
 *cur*  
 一个 `CComCurrency` 对象。  
  
### <a name="return-value"></a>返回值  
 如果第一个对象不大于或等于第二个为 FALSE，则返回 TRUE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>  Ccomcurrency:: Operator 货币  
 这些运算符用于强制转换`CComCurrency`为货币数据类型的对象。  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回对货币对象的引用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>  CComCurrency::Round  
 调用此方法要舍入到指定的小数位数的货币。  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>参数  
 *nDecimals*  
 向其位数`m_currency`将舍入，在 0 到 4 范围内。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>  CComCurrency::SetFraction  
 调用此方法以设置 `CComCurrency` 对象的小数部分。  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>参数  
 *nFraction*  
 要分配到的小数部分的值`m_currency`数据成员。 符号的小数部分必须与整数部分中，相同和的值必须在范围内 (CY_MIN_FRACTION) 是-9999 到 + 9999 (CY_MAX_FRACTION)。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>  CComCurrency::SetInteger  
 调用此方法以设置 `CComCurrency` 对象的整数部分。  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>参数  
 *nInteger*  
 要分配给的整数部分的值`m_currency`数据成员。 符号的整数部分必须匹配现有的小数部分的符号。  
  
 *nInteger*必须在范围内 CY_MIN_INTEGER 到 CY_MAX_INTEGER 非独占。 在 atlcur.h 中定义这些值。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [COleCurrency 类](../../mfc/reference/colecurrency-class.md)   
 [货币](https://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [类概述](../../atl/atl-class-overview.md)
