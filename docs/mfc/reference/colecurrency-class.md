---
title: COleCurrency 类
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: 3cb3217e02323f8a0afcd1639e6e24ee7b0f136e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366142"
---
# <a name="colecurrency-class"></a>COleCurrency 类

封装 OLE 自动化的 `CURRENCY` 数据类型。

## <a name="syntax"></a>语法

```
class COleCurrency
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle货币：COle货币](#colecurrency)|构造 `COleCurrency` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle货币：格式](#format)|生成`COleCurrency`对象的格式化字符串表示形式。|
|[COle 货币：获取状态](#getstatus)|获取此`COleCurrency`对象的状态（有效性）。|
|[COle货币：:P](#parsecurrency)|从字符串读取货币值并设置 的值`COleCurrency`。|
|[COle 货币：：设置货币](#setcurrency)|设置此`COleCurrency`对象的值。|
|[COle 货币：：设置状态](#setstatus)|设置此`COleCurrency`对象的状态（有效性）。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[运算符 |](#operator_eq)|复制值`COleCurrency`。|
|[运算符 +， -](#operator_plus_minus)|添加、减去和更改值符号`COleCurrency`。|
|[运算符 *， -]](#operator_plus_minus_eq)|从该`COleCurrency`对象中添加`COleCurrency`和减去值。|
|[操作员 */](#operator_star)|按整`COleCurrency`数值缩放值。|
|[运算符 *， /*](#operator_star_div_eq)|按整`COleCurrency`数值缩放此值。|
|[运算符 <<](#operator_stream)|将`COleCurrency`值输出到`CArchive`或`CDumpContext`。|
|[运算符 >>](#operator_stream)|从`CArchive``COleCurrency`输入对象。|
|[运算符](#operator_currency)|将`COleCurrency`值转换为货币。|
|[运算符 *、<、<等。](#colecurrency_relational_operators)|比较两`COleCurrency`个值。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COle货币：m_cur](#m_cur)|包含此`COleCurrency`对象的基础货币。|
|[COle货币：m_status](#m_status)|包含此`COleCurrency`对象的状态。|

## <a name="remarks"></a>备注

`COleCurrency`没有基类。

货币作为 8 字节、两个补数整数值（缩放为 10，000）实现。 这产生了一个定点数数字，小数点左侧有 15 位数，右侧有 4 位数。 MONEY 数据类型对于涉及资金的计算或精度很重要的任何定点计算都非常有用。 它是 OLE 自动化`VARIANT`数据类型的可能类型之一。

`COleCurrency`还实现此定点类型的一些基本算术运算。 已选择支持的操作来控制在定点计算期间发生的舍入误差。

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleCurrency`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COle货币：COle货币

构造 `COleCurrency` 对象。

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>参数

*西斯尔克*<br/>
要复制到新`COleCurrency`对象的货币值。

*库尔斯克*<br/>
要复制到`COleCurrency`新`COleCurrency`对象的现有对象。

*varSrc*<br/>
要转换为`VARIANT`货币值（VT_CY）`COleVariant`并复制到新`COleCurrency`对象的现有数据结构（可能是对象）。

*n单位**，n分数单位*指示要复制到新`COleCurrency`对象的值的单位和小数部分（在 1/10，000 中）。

### <a name="remarks"></a>备注

所有这些构造函数都创建新`COleCurrency`的对象，初始化到指定值。 下面简要介绍了每个构造函数。 除非另有说明，否则新项目`COleCurrency`的状态将设置为有效。

- COle货币（） 构造初始`COleCurrency`化为 0（零）的对象。

- COle货币（`cySrc`） 从`COleCurrency`[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)值构造对象。

- COle货币（`curSrc`） 从`COleCurrency`现有`COleCurrency`对象构造对象。 新对象的状态与源对象相同。

- COle货币（`varSrc`） 构造`COleCurrency`一个对象。 尝试将[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)结构或`COleVariant`对象转换为货币 （VT_CY） 值。 如果此转换成功，则转换后的值将复制到新`COleCurrency`对象中。 如果不是，`COleCurrency`则对象的值设置为零 （0）， 其状态无效。

- COle货币`nUnits``nFractionalUnits`（）从指定的数值分`COleCurrency`量构造对象。 如果小数零件的绝对值大于 10，000，则对单位进行适当的调整。 请注意，单位和小数部分由已签名的长值指定。

有关详细信息，请参阅 Windows SDK 中的[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)和[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)条目。

### <a name="example"></a>示例

以下示例显示了零参数和双参数构造函数的效果：

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COle货币：格式

调用此成员函数以创建货币值的格式化表示形式。

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>参数

dwFlags**<br/>
指示区域设置的标志。 只有以下标志与货币相关：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

*Lcid*<br/>
指示用于转换区域设置 ID。

### <a name="return-value"></a>返回值

`CString`包含格式化的货币值。

### <a name="remarks"></a>备注

它使用本地语言规范（区域设置的 IT）设置值格式。 货币符号不包括在返回的值中。 如果此`COleCurrency`对象的状态为 null，则返回值为空字符串。 如果状态无效，则返回字符串由字符串资源IDS_INVALID_CURRENCY指定。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COle 货币：获取状态

调用此成员函数以获取给定`COleCurrency`对象的状态（有效性）。

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>返回值

返回此值`COleCurrency`的状态。

### <a name="remarks"></a>备注

返回值由`CurrencyStatus``COleCurrency`类中定义的枚举类型定义。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleCurrency::valid`指示此`COleCurrency`对象有效。

- `COleCurrency::invalid`指示此对象`COleCurrency`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleCurrency::null`指示此`COleCurrency`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

在以下情况下，`COleCurrency`对象的状态无效：

- 如果其值从无法转换为货币值的`COleVariant`VARIANT 或值设置。

- 如果此对象在算术赋值操作期间（例如`+=`或 ） 经历了溢出或**\*** 下溢。

- 如果为此对象分配了无效值。

- 如果此对象的状态被显式设置为无效使用[SetStatus](#setstatus)。

有关可能将状态设置为无效的操作的详细信息，请参阅以下成员函数：

- [COleCurrency](#colecurrency)

- [运算符 |](#operator_eq)

- [运算符 = -](#operator_plus_minus)

- [运算符 * 和 -}](#operator_plus_minus_eq)

- [运算符 = /](#operator_star)

- [运算符 * 和 /*](#operator_star_div_eq)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COle货币：m_cur

此`COleCurrency`对象的基础[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)结构。

### <a name="remarks"></a>备注

> [!CAUTION]
> 更改此函数返回的`CURRENCY`指针访问的结构中的值将更改此`COleCurrency`对象的值。 它不会更改此`COleCurrency`对象的状态。

有关详细信息，请参阅 Windows SDK 中的["货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)"条目。

## <a name="colecurrencym_status"></a><a name="m_status"></a>COle货币：m_status

此数据成员的类型是枚举类型`CurrencyStatus`，在类中`COleCurrency`定义。

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>备注

有关这些状态值的简要说明，请参阅以下列表：

- `COleCurrency::valid`指示此`COleCurrency`对象有效。

- `COleCurrency::invalid`指示此对象`COleCurrency`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleCurrency::null`指示此`COleCurrency`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

在以下情况下，`COleCurrency`对象的状态无效：

- 如果其值从无法转换为货币值的`COleVariant`VARIANT 或值设置。

- 如果此对象在算术赋值操作期间（例如`+=`或 ） 经历了溢出或**\*** 下溢。

- 如果为此对象分配了无效值。

- 如果此对象的状态被显式设置为无效使用[SetStatus](#setstatus)。

有关可能将状态设置为无效的操作的详细信息，请参阅以下成员函数：

- [COleCurrency](#colecurrency)

- [运算符 |](#operator_eq)

- [运算符 +， -](#operator_plus_minus)

- [运算符 *， -]](#operator_plus_minus_eq)

- [操作员 */](#operator_star)

- [运算符 *， /*](#operator_star_div_eq)

> [!CAUTION]
> 此数据成员适用于高级编程情况。 应使用内联成员函数["获取状态"](#getstatus)和["设置状态](#setstatus)"。 有关`SetStatus`显式设置此数据成员的进一步注意事项，请参阅。

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COle货币：：运算符 |

这些重载赋值运算符将源币种值复制到`COleCurrency`此对象中。

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>备注

每个运算符的简要描述如下：

- **运算符 *（** `cySrc` **）** 该`CURRENCY`值将复制到对象中`COleCurrency`，其状态设置为有效。

- **运算符 *（** `curSrc` **）** 操作数的值和状态，将现有`COleCurrency`对象复制到此`COleCurrency`对象中。

- 运算符 **（varSrc* **operator =(** **）** 如果`VARIANT`将值（或[COleVariant](../../mfc/reference/colevariant-class.md)对象）转换为货币 （ `VT_CY`） 成功，则转换的值将复制到此`COleCurrency`对象，其状态设置为有效。 如果转换不成功，`COleCurrency`则对象的值设置为 0，其状态设置为无效。

有关详细信息，请参阅 Windows SDK 中的[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)和[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)条目。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COle货币：：运算符 +， -

这些运算符允许您相互添加和减去两`COleCurrency`个`COleCurrency`值，并更改值的符号。

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>备注

如果任一操作数为空，则结果`COleCurrency`值的状态为 null。

如果算术运算溢出，则生成的`COleCurrency`值无效。

如果操作数无效，另一个不为空，则生成的`COleCurrency`值的状态无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COle货币：：运算符 *，-*

允许您在此`COleCurrency`对象中添加和减去`COleCurrency`值。

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>备注

如果任一操作数为空，则此`COleCurrency`对象的状态设置为 null。

如果算术运算溢出，则此`COleCurrency`对象的状态设置为无效。

如果任一操作数无效，另一个操作数不为空，则此`COleCurrency`对象的状态设置为无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COle货币：：操作员\*和/

允许您按整数值缩放`COleCurrency`值。

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>备注

如果`COleCurrency`操作数为 null，则结果`COleCurrency`值的状态为 null。

如果算术运算溢出或下溢，则结果`COleCurrency`值的状态无效。

如果`COleCurrency`操作数无效，则结果`COleCurrency`值的状态无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COle货币：：运算符\*= 、 /=

允许您按整数值缩放`COleCurrency`此值。

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>备注

如果`COleCurrency`操作数为 null，则此`COleCurrency`对象的状态设置为 null。

如果算术运算溢出，则此`COleCurrency`对象的状态设置为无效。

如果`COleCurrency`操作数无效，则此`COleCurrency`对象的状态设置为无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COle货币：运算符&lt;&lt;，&gt;&gt;

支持诊断转储并存储到存档。

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>备注

提取 （ **>>**） 运算符支持从存档加载。

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COle货币：：操作员货币

返回其`CURRENCY`值从此`COleCurrency`对象复制的结构。

```
operator CURRENCY() const;
```

### <a name="remarks"></a>备注

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COle货币：:P

调用此成员函数以分析字符串以读取货币值。

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>参数

*lpsz货币*<br/>
指向要解析的 null 终止字符串的指针。

dwFlags**<br/>
指示区域设置的标志，可能为以下标志：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

*Lcid*<br/>
指示用于转换区域设置 ID。

### <a name="return-value"></a>返回值

如果字符串已成功转换为货币值，则非零，否则为 0。

### <a name="remarks"></a>备注

它使用本地语言规范（区域设置 ID）来表示源字符串中非数字字符的含义。

有关区域设置 ID 值的讨论，请参阅[支持多种语言](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages)。

如果字符串已成功转换为货币值，则此`COleCurrency`对象的值将设置为该值，其状态将有效。

如果字符串无法转换为货币值，或者存在数字溢出，则此`COleCurrency`对象的状态无效。

如果字符串转换由于内存分配错误而失败，此函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。 在任何其他错误状态下，此函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>COle货币关系运算符

比较两个货币值，如果条件为 true，则返回非零;否则 0。

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 如果操作数的状态为 null**<** 或**\<** 无效**>**，则排序操作 （、、、、）**>=** 的返回值未定义。 相等运算符 （ `==` `!=`、 ） 考虑操作数的状态。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COle 货币：：设置货币

调用此成员函数以设置此`COleCurrency`对象的单位和小数部分。

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>参数

*n单位**，n分数单位*指示要复制到此`COleCurrency`对象的值的单位和小数部分（在 1/10，000 中）。

### <a name="remarks"></a>备注

如果小数部分的绝对值大于 10，000，则对单位进行适当的调整，如以下示例的第三个所示。

请注意，单位和小数部分由已签名的长值指定。 以下示例的第四个示例显示了参数具有不同符号时发生的情况。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COle 货币：：设置状态

调用此成员函数以设置此`COleCurrency`对象的状态（有效性）。

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>参数

*状态*<br/>
此`COleCurrency`对象的新状态。

### <a name="remarks"></a>备注

*状态*参数值由`CurrencyStatus`枚举类型定义，该类型在类中`COleCurrency`定义。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleCurrency::valid`指示此`COleCurrency`对象有效。

- `COleCurrency::invalid`指示此对象`COleCurrency`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleCurrency::null`指示此`COleCurrency`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

> [!CAUTION]
> 此功能适用于高级编程情况。 此函数不会更改此对象中的数据。 它最常用于将状态设置为 null 或无效。 请注意，赋值运算符 （[运算符 =](#operator_eq)） 和[SetCurrency](#setcurrency)会根据源值将对象的状态设置为 。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 类](../../mfc/reference/colevariant-class.md)
