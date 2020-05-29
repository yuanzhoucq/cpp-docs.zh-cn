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
ms.openlocfilehash: 331b89ff118f727303e887670960ee6078b01fb1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747083"
---
# <a name="cpoint-class"></a>CPoint 类

类似于 Windows `POINT` 结构。

## <a name="syntax"></a>语法

```
class CPoint : public tagPOINT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPoint：CPoint](#cpoint)|构造一个 `CPoint`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPoint：偏移](#offset)|将值添加到`x`和`y`中`CPoint`。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CPoint：：运算符 -](#operator_-)|返回 和`CPoint`大小的差异，或点的否定，或两个点之间的大小差异，或由负大小的偏移。|
|[CPoint：：操作员！*](#operator_neq)|检查两点之间的不平等。|
|[CPoint：：运算符 |](#operator_add)|返回 和`CPoint`大小或点的总和，或`CRect`偏移大小。|
|[CPoint：：运算符 |](#operator_add_eq)|`CPoint`通过添加大小或点进行偏移。|
|[CPoint：：运算符 -*](#operator_-_eq)|`CPoint`通过减去大小或点来偏移。|
|[CPoint：：运算符 |](#operator_eq_eq)|检查两点之间的相等性。|

## <a name="remarks"></a>备注

它还包括要操作`CPoint`的成员函数和[POINT](/windows/win32/api/windef/ns-windef-point)结构。

对象`CPoint`可以在使用结构的任何位置`POINT`使用。 与"大小"交互的此类运算符接受[CSize](../../atl-mfc-shared/reference/csize-class.md)对象或[SIZE](/windows/win32/api/windef/ns-windef-size)结构，因为两者是可互换的。

> [!NOTE]
> 此类派生自结构`tagPOINT`。 （名称`tagPOINT`是`POINT`结构不太常用的名称。这意味着`POINT`结构的数据成员`x`和`y`是 的`CPoint`可访问数据成员。

> [!NOTE]
> 有关共享实用程序类的详细信息（如`CPoint`），请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagPOINT`

`CPoint`

## <a name="requirements"></a>要求

**标题：** atltype.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint：CPoint

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
[POINT](/windows/win32/api/windef/ns-windef-point)结构`CPoint`或指定用于初始化`CPoint`的值。

*initSize*<br/>
[指定](/windows/win32/api/windef/ns-windef-size)用于初始化`CPoint`的值的大小结构或[CSize。](../../atl-mfc-shared/reference/csize-class.md)

*dwPoint*<br/>
将`x`成员设为*dwPoint*的低阶字，将`y`成员设到*dwPoint*的高阶字。

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

## <a name="cpointoffset"></a><a name="offset"></a>CPoint：偏移

将值添加到`x`和`y`中`CPoint`。

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>参数

*x 偏移*<br/>
指定要偏移`x`的成员的金额`CPoint`。

*yOffset*<br/>
指定要偏移`y`的成员的金额`CPoint`。

*点*<br/>
指定要偏移的`CPoint`量`CPoint`（ [POINT](/windows/win32/api/windef/ns-windef-point)或 ）。

size <br/>
指定要偏移的`CPoint`量[（SIZE](/windows/win32/api/windef/ns-windef-size)或["大小](../../atl-mfc-shared/reference/csize-class.md)"）。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint：：运算符 |

检查两点之间的相等性。

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>参数

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或`CPoint`对象。

### <a name="return-value"></a>返回值

如果点相等，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint：：操作员！*

检查两点之间的不平等。

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>参数

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或`CPoint`对象。

### <a name="return-value"></a>返回值

如果点不相等，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint：：运算符 |

第一个重载向 添加`CPoint`大小到 。

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>参数

size <br/>
包含[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="remarks"></a>备注

第二个重载向 添加`CPoint`点到 。

在这两种情况下，添加是通过将右侧操作数`x`的成员`cx`（或`x`） 成员添加到 右侧`CPoint`操作数的成员，并将`y`右侧操作数的`cy`（或 ） 成员添加到`y`成员。 `CPoint`

例如，添加到`CPoint(5, -7)`包含的`CPoint(30, 40)`变量将变量更改为`CPoint(35, 33)`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint：：运算符 -*

第一个重载从 中减去`CPoint`大小。

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>参数

size <br/>
包含[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="remarks"></a>备注

第二个重载从 中减去`CPoint`一个点。

在这两种情况下，减法是通过从 中减去右侧`x`操作数`cx``x`的成员（或 ）`CPoint`成员，并从`y``cy``y`中减去右侧操作数的成员来完成。 `CPoint`

例如，从包含的`CPoint(5, -7)``CPoint(30, 40)`变量中减去将变量更改为`CPoint(25, 47)`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint：：运算符 |

使用此运算符`CPoint`可以偏移 或`CPoint``CSize`对象，或者由 偏移`CRect``CPoint`。

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>参数

size <br/>
包含[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

*lpRect*<br/>
包含指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针。

### <a name="return-value"></a>返回值

由`CPoint`大小偏移的 a、由点`CPoint`偏移的 a 或`CRect`偏移点。

### <a name="remarks"></a>备注

例如，使用前两个重载之`CPoint(25, -19)`一按点`CPoint(15, 5)`或大小`CSize(15, 5)`偏移点将返回值`CPoint(40, -14)`。

将矩形添加到点返回矩形后偏移在点中指定的`x`和`y`值。 例如，使用最后一个重载来偏移矩形`CRect(125, 219, 325, 419)`的点`CPoint(25, -19)`返回`CRect(150, 200, 350, 400)`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint：：运算符 -

使用前两个重载之一从`CPoint``CSize``CPoint`中减去 或 对象。

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>参数

*点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

size <br/>
[大小](/windows/win32/api/windef/ns-windef-size)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针。

### <a name="return-value"></a>返回值

A`CSize`是两个点之间的差异，一个`CPoint`被大小否定所抵消，一个是`CRect`被点否定所抵消的，或者是`CPoint`点的否定。

### <a name="remarks"></a>备注

第三个重载`CRect`通过否定偏移`CPoint`a。 最后，使用一元运算符否定`CPoint`。

例如，使用第一个重载来查找两个点`CPoint(25, -19)`和`CPoint(15, 5)`返回`CSize(10, -24)`之间的差异。

`CSize`从中`CPoint`减去 执行与上述相同的计算，但返回`CPoint`对象，而不是`CSize`对象。 例如，使用第二个重载查找点`CPoint(25, -19)`和大小`CSize(15, 5)`之间的差值返回`CPoint(10, -24)`。

从点中减去矩形返回由点中指定的`x`和`y`值的底数偏移的矩形。 例如，使用最后一个重载按点`CRect(125, 200, 325, 400)``CPoint(25, -19)`偏移矩形返回`CRect(100, 219, 300, 419)`。

使用一元运算符否定点。 例如，使用带有点的`CPoint(25, -19)`一元运算符返回`CPoint(-25, 19)`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[点结构](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize 类](../../atl-mfc-shared/reference/csize-class.md)
