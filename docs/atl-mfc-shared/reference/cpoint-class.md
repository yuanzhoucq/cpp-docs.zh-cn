---
title: CPoint 类
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: b7c13ef8b9656c5c2fa6a90fefca0d9babbe1c84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491225"
---
# <a name="cpoint-class"></a>CPoint 类

类似于 Windows `POINT` 结构。

## <a name="syntax"></a>语法

```
class CPoint : public tagPOINT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPoint：： CPoint](#cpoint)|构造一个 `CPoint`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPoint::Offset](#offset)|将值添加到`x`的`y`和成员`CPoint`。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CPoint：： operator-](#operator_-)|返回`CPoint`和大小的差，或点的求反或两个点之间的大小差或负大小的偏移量。|
|[CPoint：： operator！ =](#operator_neq)|检查两个点之间是否不相等。|
|[CPoint：： operator +](#operator_add)|返回与大小或点的和， `CRect`或大小的偏移量。 `CPoint`|
|[CPoint：： operator + =](#operator_add_eq)|添加`CPoint`大小或点后的偏移量。|
|[CPoint::operator -=](#operator_-_eq)|通过`CPoint`减去大小或点来偏移。|
|[CPoint：： operator = =](#operator_eq_eq)|检查两个点之间是否相等。|

## <a name="remarks"></a>备注

它还包括用于处理`CPoint`和[点](/windows/win32/api/windef/ns-windef-point)结构的成员函数。

对象可以在使用`POINT`结构的任何位置使用。 `CPoint` 此类的与 "size" 交互的运算符接受[CSize](../../atl-mfc-shared/reference/csize-class.md)对象或[大小](/windows/win32/api/windef/ns-windef-size)结构，因为这两个对象是可互换的。

> [!NOTE]
>  此类派生自`tagPOINT`结构。 （名称`tagPOINT`是`POINT`结构的常用名称。）这意味着`POINT` `CPoint`结构的数据成员`y` `x`和可访问的数据成员。

> [!NOTE]
>  有关共享实用工具类（如`CPoint`）的详细信息，请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagPOINT`

`CPoint`

## <a name="requirements"></a>要求

**标头：** atltypes

##  <a name="cpoint"></a>CPoint：： CPoint

构造 `CPoint` 对象。

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>参数

*initX*<br/>
指定 `x` 的 `CPoint` 成员的值。

*initY*<br/>
指定 `y` 的 `CPoint` 成员的值。

*initPt*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)结构或`CPoint`指定用于初始化`CPoint`的值的。

*initSize*<br/>
指定用于初始化 `CPoint`的值的[大小](/windows/win32/api/windef/ns-windef-size)结构或 [CSize](../../atl-mfc-shared/reference/csize-class.md)。

*dwPoint*<br/>
将成员设置为`y` *dwPoint*的低序位字，并将成员设置为 dwPoint 的高序位字。 `x`

### <a name="remarks"></a>备注

如果未提供自变量，则 `x` 和 `y` 成员将设置为 0。

### <a name="example"></a>示例

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

##  <a name="offset"></a>CPoint：： Offset

将值添加到`x`的`y`和成员`CPoint`。

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>参数

*xOffset*<br/>
指定的`x`成员`CPoint`的偏移量。

*yOffset*<br/>
指定的`y`成员`CPoint`的偏移量。

*point*<br/>
指定要偏移的`CPoint`量（ `CPoint`[点](/windows/win32/api/windef/ns-windef-point)或）。

*size*<br/>
指定要偏移的`CPoint`量（[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](../../atl-mfc-shared/reference/csize-class.md)）。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CPoint：： operator = =

检查两个点之间是否相等。

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>参数

*point*<br/>
包含[点](/windows/win32/api/windef/ns-windef-point)结构或`CPoint`对象。

### <a name="return-value"></a>返回值

如果点相等，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>CPoint：： operator！ =

检查两个点之间是否不相等。

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>参数

*point*<br/>
包含[点](/windows/win32/api/windef/ns-windef-point)结构或`CPoint`对象。

### <a name="return-value"></a>返回值

如果点不相等，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>CPoint：： operator + =

第一个重载向添加一个大小`CPoint`。

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>参数

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*point*<br/>
包含[点](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="remarks"></a>备注

第二个重载将一个点添加`CPoint`到。

在这两种情况下，加法是通过`x`将右`cx`操作数的（或）成员添加到`x`的`CPoint`成员并将右操作数的`y` （或`cy`）成员添加到`y` 的`CPoint`成员。

例如，将添加`CPoint(5, -7)`到包含`CPoint(30, 40)`变量`CPoint(35, 33)`更改的变量。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>CPoint：： operator-=

第一个重载从中`CPoint`减去一个大小。

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>参数

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*point*<br/>
包含[点](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="remarks"></a>备注

第二个重载从中`CPoint`减去一个点。

在这两种情况下，可通过从`x` `CPoint` `x`的成员`cx`减去右侧操作数的（或）成员并减去右侧的`y` （或`cy`）成员，来实现减法运算。`y`的成员的操作数`CPoint`。

例如，从包含`CPoint(5, -7)` `CPoint(30, 40)`变量`CPoint(25, 47)`更改的变量中减去。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>CPoint：： operator +

使用此`CPoint`运算符可`CPoint`由或`CSize` 对象偏移`CRect` ，或用于的偏移量。 `CPoint`

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>参数

*size*<br/>
包含[大小](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*point*<br/>
包含[点](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

*lpRect*<br/>
包含指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针。

### <a name="return-value"></a>返回值

偏移大小、由点偏移或`CRect`由点偏移的偏移量。 `CPoint` `CPoint`

### <a name="remarks"></a>备注

例如，使用前两个重载`CPoint(25, -19)`之一来使点`CPoint(15, 5)`与点或大小`CSize(15, 5)`偏移，返回值`CPoint(40, -14)`。

将矩形添加到某个点后，该矩形会在偏移后`x`返回`y`在该点中指定的和值。 例如，使用最后一个重载通过点`CRect(125, 219, 325, 419)` `CPoint(25, -19)`偏移矩形会返回`CRect(150, 200, 350, 400)`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>CPoint：： operator-

使用前两个重载之一来从中`CPoint` `CPoint`减去或`CSize`对象。

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>参数

*point*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

*size*<br/>
[大小](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针。

### <a name="return-value"></a>返回值

一个`CSize` ，它是两个点之间的差异`CPoint` ，偏移一个大小的求反，一个`CRect`是一个点的取反的偏移量，或者`CPoint`是一个点的求反。

### <a name="remarks"></a>备注

第三个重载`CRect`按的`CPoint`求反。 最后，使用一元运算符进行反`CPoint`运算。

例如，使用第一个重载查找两个点`CPoint(25, -19)`之间的差异，并`CPoint(15, 5)`返回。 `CSize(10, -24)`

从中`CPoint`减去与上述相同的计算，但返回`CPoint`对象，而不是`CSize`对象。 `CSize` 例如，使用第二个重载查找点`CPoint(25, -19)`和`CPoint(10, -24)`大小`CSize(15, 5)`之间的差异。

从某个点减去一个矩形将以该点中指定的`x`和`y`值的负值作为偏移量。 例如，使用最后一个重载按点`CRect(125, 200, 325, 400)` `CPoint(25, -19)`偏移矩形时返回`CRect(100, 219, 300, 419)`。

使用一元运算符对某个点求反。 例如，将一元运算符与点`CPoint(25, -19)`一起使用时，将返回。 `CPoint(-25, 19)`

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[点结构](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize 类](../../atl-mfc-shared/reference/csize-class.md)
