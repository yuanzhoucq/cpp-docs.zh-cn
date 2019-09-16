---
title: CSize 类
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491654"
---
# <a name="csize-class"></a>CSize 类

类似于实现相对坐标或位置的 Windows [SIZE](/windows/win32/api/windef/ns-windef-size) 结构。

## <a name="syntax"></a>语法

```
class CSize : public tagSIZE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSize：： CSize](#csize)|构造 `CSize` 对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSize：： operator-](#operator_-)|减去两个大小。|
|[CSize：： operator！ =](#operator_neq)|检查和大小之间`CSize`的不相等。|
|[CSize：： operator +](#operator_add)|添加两种大小。|
|[CSize：： operator + =](#operator_add_eq)|向添加大小`CSize`。|
|[CSize::operator -=](#operator_-_eq)|从中`CSize`减去一个大小。|
|[CSize：： operator = =](#operator_eq_eq)|检查`CSize`和大小是否相等。|

## <a name="remarks"></a>备注

此类派生自`SIZE`结构。 这`CSize`意味着，可以在调用`SIZE`的参数中传递，该`SIZE`结构的数据成员可以访问数据成员`CSize`。

`SIZE` `cy` `cx` （和`CSize`）的和成员是公共的。 此外， `CSize`还实现了`SIZE`成员函数以操作结构。

> [!NOTE]
> 有关共享实用工具类（如`CSize`）的详细信息，请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagSIZE`

`CSize`

## <a name="requirements"></a>要求

**标头：** atltypes

##  <a name="csize"></a>CSize：： CSize

构造 `CSize` 对象。

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>参数

*initCX*<br/>
设置的`CSize`成员。 `cx`

*initCY*<br/>
设置的`CSize`成员。 `cy`

*initSize*<br/>
用于 初始化[的](/windows/win32/api/windef/ns-windef-size)大小`CSize`结构或`CSize`对象。

*initPt*<br/>
[点](/windows/win32/api/windef/ns-windef-point)结构或`CPoint`用于初始化`CSize`的对象。

*dwSize*<br/>
用于初始化`CSize`的 DWORD。 低序位字是`cx`成员，高位字`cy`是成员。

### <a name="remarks"></a>备注

如果未提供任何参数， `cx` `cy`则将其初始化为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CSize：： operator = =

检查两个大小是否相等。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>备注

如果大小相等，则返回非零值 otherwize 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize：： operator！ =

检查两个大小是否不相等。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>备注

如果大小不相等，则返回非零值，否则返回0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize：： operator + =

将大小添加到此`CSize`。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize：： operator-=

从此中`CSize`减去大小。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize：： operator +

这些运算符将此`CSize`值添加到参数的值。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>备注

请参阅以下各个运算符的说明：

- **operator +(** *size* **)**

  此操作会将`CSize`两个值相加。

- **operator +(** *point* **)**

  此操作通过此`CSize`值偏移（移动）[点](/previous-versions/dd162805\(v=vs.85\))（或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)）值。 此`cx` `x` 值的`POINT`和`cy`成员将添加到值的和`y`数据成员中。 `CSize` 它类似于采用[大小](/windows/win32/api/windef/ns-windef-size)参数的[CPoint：： operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)的版本。

- **operator +(** *lpRect* **)**

   此操作通过此`CSize`值偏移（移动）[矩形](/previous-versions/dd162897\(v=vs.85\))（或[CRect](../../atl-mfc-shared/reference/crect-class.md)）值。 此`cx` `cy` `left` `RECT` `top` `bottom`值的和成员将添加到值的、、 `right`和数据成员中。 `CSize` 它类似于采用[大小](/windows/win32/api/windef/ns-windef-size)参数的[CRect：： operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)的版本。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize：： operator-

其中的前三个运算符将此`CSize`值减去到参数的值。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>备注

第四个运算符（一元减号）更改`CSize`值的符号。 请参阅以下各个运算符的说明：

- **operator -(** *size* **)**

  此操作会将`CSize`两个值相减。

- **operator -(** *point* **)**

  此操作通过此`CSize`值的加法逆值偏移（移动）一个[点](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)值。 此`cx` `cy` `x`值的和将从`POINT`值的和`y`数据成员中减去。 `CSize` 它类似于采用[大小](/windows/win32/api/windef/ns-windef-size)参数的[CPoint：： operator](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)的版本。

- **operator -(** *lpRect* **)**

  此操作通过此`CSize`值的加法反转偏移（移动）[矩形](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)值。 此`cx` `cy` `left` `top`值的和成员从值`RECT`的、、 `right`和`bottom`数据成员中减去。 `CSize` 它类似于采用[大小](/windows/win32/api/windef/ns-windef-size)参数的[CRect：： operator](../../atl-mfc-shared/reference/crect-class.md#operator_-)的版本。

- **operator -()**

  此操作返回此`CSize`值的加法逆元。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 类](../../atl-mfc-shared/reference/cpoint-class.md)
