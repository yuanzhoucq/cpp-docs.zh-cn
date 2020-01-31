---
title: CRect 类
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: 13f86c411cca98f5817d1b3b2d9162ae8af8b734
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821364"
---
# <a name="crect-class"></a>CRect 类

类似于 Windows [RECT](/windows/win32/api/windef/ns-windef-rect)结构。

## <a name="syntax"></a>语法

```
class CRect : public tagRECT
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CRect::CRect](#crect)|构造 `CRect` 对象。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|返回 `CRect`的右下点。|
|[CRect::CenterPoint](#centerpoint)|返回 `CRect`的 centerpoint。|
|[CRect::CopyRect](#copyrect)|将源矩形的维度复制到 `CRect`。|
|[CRect::DeflateRect](#deflaterect)|减小 `CRect`的宽度和高度。|
|[CRect::EqualRect](#equalrect)|确定 `CRect` 是否等于给定矩形。|
|[CRect::Height](#height)|计算 `CRect`的高度。|
|[CRect::InflateRect](#inflaterect)|增加 `CRect`的宽度和高度。|
|[CRect::IntersectRect](#intersectrect)|将 `CRect` 设置为等于两个矩形的交集。|
|[CRect::IsRectEmpty](#isrectempty)|确定 `CRect` 是否为空。 如果宽度和/或高度均为0，则 `CRect` 为空。|
|[CRect::IsRectNull](#isrectnull)|确定 `top`、`bottom`、`left`和 `right` 成员变量是否均等于0。|
|[CRect::MoveToX](#movetox)|将 `CRect` 移到指定的 x 坐标。|
|[CRect::MoveToXY](#movetoxy)|将 `CRect` 移动到指定的 x 坐标和 y 坐标。|
|[CRect::MoveToY](#movetoy)|将 `CRect` 移动到指定的 y 坐标。|
|[CRect::NormalizeRect](#normalizerect)|标准化 `CRect`的高度和宽度。|
|[CRect::OffsetRect](#offsetrect)|按指定的偏移量移动 `CRect`。|
|[CRect::PtInRect](#ptinrect)|确定指定点是否位于 `CRect`中。|
|[CRect::SetRect](#setrect)|设置 `CRect`的尺寸。|
|[CRect::SetRectEmpty](#setrectempty)|将 `CRect` 设置为一个空矩形（所有坐标都等于0）。|
|[CRect::Size](#size)|计算 `CRect`的大小。|
|[CRect::SubtractRect](#subtractrect)|从一个矩形中减去另一个。|
|[CRect::TopLeft](#topleft)|返回 `CRect`的左上角点。|
|[CRect::UnionRect](#unionrect)|将 `CRect` 设置为等于两个矩形的并集。|
|[CRect::Width](#width)|计算 `CRect`的宽度。|

### <a name="public-operators"></a>公用運算子

|Name|描述|
|----------|-----------------|
|[CRect：： operator-](#operator_-)|从 `CRect` 或压缩 `CRect` 中减去给定偏移量，并返回生成的 `CRect`。|
|[CRect：： operator LPCRECT](#operator_lpcrect)|将 `CRect` 转换为 `LPCRECT`。|
|[CRect：： operator LPRECT](#operator_lprect)|将 `CRect` 转换为 `LPRECT`。|
|[CRect::operator !=](#operator_neq)|确定 `CRect` 是否不等于矩形。|
|[CRect：： operator &amp;](#operator_amp)|创建 `CRect` 和矩形的交集，并返回生成的 `CRect`。|
|[CRect：： operator &amp;=](#operator_amp_eq)|将 `CRect` 设置为等于 `CRect` 与矩形的交集。|
|[CRect：： operator&#124;](#operator_or)|创建 `CRect` 和矩形的并集，并返回生成的 `CRect`。|
|[CRect::operator &#124;=](#operator_or_eq)|将 `CRect` 等于 `CRect` 和矩形的并集。|
|[CRect：： operator +](#operator_add)|将给定偏移量添加到 `CRect` 或增加 `CRect` 并返回生成的 `CRect`。|
|[CRect：： operator + =](#operator_add_eq)|将指定偏移量添加到 `CRect` 或增加 `CRect`。|
|[CRect：： operator =](#operator_eq)|将矩形的尺寸复制到 `CRect`。|
|[CRect::operator -=](#operator_-_eq)|从 `CRect` 或压缩 `CRect`中减去指定偏移量。|
|[CRect：： operator = =](#operator_eq_eq)|确定 `CRect` 是否等于矩形。|

## <a name="remarks"></a>备注

`CRect` 还包括用于处理 `CRect` 对象和 Windows `RECT` 结构的成员函数。

可以将 `CRect` 对象作为函数参数传递，只要可以传递 `RECT` 结构、`LPCRECT`或 `LPRECT` 即可。

> [!NOTE]
> 此类派生自 `tagRECT` 结构。 （名称 `tagRECT` 是 `RECT` 结构的常用名称。）这意味着 `RECT` 结构的数据成员（`left`、`top`、`right`和 `bottom`）是 `CRect`可访问的数据成员。

`CRect` 包含定义矩形的左上角和右下角的成员变量。

当指定 `CRect`时，您必须仔细构造它，以便对其进行规范化，也就是说，左坐标的值小于右侧，而顶部小于底部。 例如，左上角（10，10）和右下方（20，20）定义一个规范化矩形，但左上角（20，20）和右下方（10，10）定义了一个非规范化矩形。 如果矩形未规范化，则很多 `CRect` 成员函数可能会返回不正确的结果。 （有关这些函数的列表，请参阅[CRect：： NormalizeRect](#normalizerect) 。）在调用需要规范化矩形的函数之前，可以通过调用 `NormalizeRect` 函数来规范化非规范化矩形。

使用[cdc：:D ptolp](../../mfc/reference/cdc-class.md#dptolp)和[Cdc：： LPtoDP](../../mfc/reference/cdc-class.md#lptodp)成员函数处理 `CRect` 时要格外小心。 如果显示上下文的映射模式为 y 范围为负数，如 `MM_LOENGLISH`中所示，则 `CDC::DPtoLP` 将转换 `CRect`，使其顶部大于底部。 然后，诸如 `Height` 和 `Size` 之类的函数将为转换后的 `CRect`的高度返回负值，并且矩形将为非规范化。

使用重载 `CRect` 运算符时，第一个操作数必须是 `CRect`;第二个可以是[矩形](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect` 的对象。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagRECT`

`CRect`

## <a name="requirements"></a>需求

**标头：** atltypes

##  <a name="bottomright"></a>CRect：： BottomRight

坐标作为对 `CRect`中所包含的[CPoint](cpoint-class.md)对象的引用返回。

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>返回值

矩形右下角的坐标。

### <a name="remarks"></a>备注

可以使用此函数获取或设置矩形的右下角。 通过在赋值运算符的左侧使用此函数设置角。

### <a name="example"></a>示例

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

##  <a name="centerpoint"></a>CRect：： CenterPoint

通过添加左值和右值并除以2来计算 `CRect` 的 centerpoint，并添加前和后值并除以2。

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>返回值

作为 `CRect`centerpoint 的 `CPoint` 对象。

### <a name="example"></a>示例

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

##  <a name="copyrect"></a>CRect：： CopyRect

将 `lpSrcRect` 矩形复制到 `CRect`中。

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>参数

*lpSrcRect*<br/>
指向要复制的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect` 的对象。

### <a name="example"></a>示例

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

##  <a name="crect"></a>CRect：： CRect

构造 `CRect` 对象。

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>参数

*l*<br/>
指定 `CRect`的左侧位置。

*t*<br/>
指定 `CRect`的顶部。

*r*<br/>
指定 `CRect`的正确位置。

*b*<br/>
指定 `CRect`的底部。

*srcRect*<br/>
引用坐标为 [的](/windows/win32/api/windef/ns-windef-rect)矩形`CRect`结构。

*lpSrcRect*<br/>
指向包含 `CRect`坐标的 `RECT` 结构。

*point*<br/>
指定要构造的矩形的原点。 对应于左上角。

*size*<br/>
指定要构造的矩形从左上角到右下角的位移。

*topLeft*<br/>
指定 `CRect`的左上角位置。

*bottomRight*<br/>
指定 `CRect`的右下角位置。

### <a name="remarks"></a>备注

如果未提供任何参数，则不会初始化 `left`、`top`、`right`和 `bottom` 成员。

`CRect`（`const RECT&`）和 `CRect`（`LPCRECT`）构造函数执行[CopyRect](#copyrect)。 其他构造函数直接初始化对象的成员变量。

### <a name="example"></a>示例

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

##  <a name="deflaterect"></a>  CRect::DeflateRect

通过将压缩的边向中心移动来 `DeflateRect` `CRect`。

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
指定 `CRect`左右两侧 deflate 的单位数。

*y*<br/>
指定 `CRect`的上和下 deflate 的单位数。

*size*<br/>
一个[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](csize-class.md) ，指定要对其进行 deflate `CRect`的单位数。 `cx` 值指定左边缘和右边缘的单位数，`cy` 值指定顶部和底部要 deflate 的单位数。

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect`，它指定每一侧 deflate 的单位数。

*l*<br/>
指定 `CRect`左侧 deflate 的单位数。

*t*<br/>
指定 `CRect`顶部 deflate 的单位数。

*r*<br/>
指定 `CRect`右侧 deflate 的单位数。

*b*<br/>
指定 `CRect`底部 deflate 的单位数。

### <a name="remarks"></a>备注

为此，`DeflateRect` 将单元添加到左侧和顶部，并从右侧和底部减去单元。 `DeflateRect` 的参数是有符号值;正值 deflate `CRect` 值和负值将其在一起。

前两个重载 deflate `CRect` 的两对方，使其总宽度降低2倍*x* （或 `cx`），其总高度将减少两*倍（或*`cy`）。 另外两个重载分别 deflate `CRect` 的每一方。

### <a name="example"></a>示例

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

##  <a name="equalrect"></a>CRect：： EqualRect

确定 `CRect` 是否等于给定矩形。

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向[矩形结构或](/windows/win32/api/windef/ns-windef-rect)`CRect` 对象，该对象包含矩形的左上角和右下角坐标。

### <a name="return-value"></a>返回值

如果两个矩形具有相同的上、左、下和右两个值，则为非零值;否则为0。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

##  <a name="height"></a>CRect：： Height

通过从底部值中减去顶部值来计算 `CRect` 的高度。

```
int Height() const throw();
```

### <a name="return-value"></a>返回值

`CRect`的高度。

### <a name="remarks"></a>备注

结果值可以为负数。

> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>  CRect::InflateRect

`InflateRect` 通过将增加的边从中心移动来 `CRect`。

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
指定 `CRect`左右两侧的单位数。

*y*<br/>
指定 `CRect`的顶部和底部的单位数。

*size*<br/>
一个[大小](/windows/win32/api/windef/ns-windef-size)或[CSize](csize-class.md) ，用于指定 `CRect`的单位数。 `cx` 值指定向左和向右的单位数，`cy` 值指定顶部和底部的单位数。

*lpRect*<br/>
指向一个[RECT](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect`，它指定每一侧的单位数。

*l*<br/>
指定 `CRect`左侧的单位数。

*t*<br/>
指定 `CRect`顶部的单位数。

*r*<br/>
指定 `CRect`右侧的单位数。

*b*<br/>
指定 `CRect`底部的单位数。

### <a name="remarks"></a>备注

为此，`InflateRect` 从左到上减去单位，并向右和向下添加单位。 `InflateRect` 的参数是有符号值;正值会将 `CRect`，负值 deflate。

前两个重载将两对 `CRect` 相反，使其总宽度增加两倍*x* （或 `cx`），其总高度增加了两*倍（或*`cy`）。 另外两个重载将 `CRect` 的每一方与其他重载一起膨胀。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>  CRect::IntersectRect

使 `CRect` 等于两个现有矩形的交集。

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>参数

*lpRect1*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)结构或包含源矩形的 `CRect` 对象。

*lpRect2*<br/>
指向 `RECT` 结构或包含源矩形的 `CRect` 对象。

### <a name="return-value"></a>返回值

如果交集不为空，则为非零值;如果交集为空，则为0。

### <a name="remarks"></a>备注

交集是两个现有矩形中包含的最大矩形。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

##  <a name="isrectempty"></a>CRect：： IsRectEmpty

确定 `CRect` 是否为空。

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果 `CRect` 为空，则为非零值;如果 `CRect` 不为空，则为0。

### <a name="remarks"></a>备注

如果宽度和/或高度为0或负数，则矩形为空。 与 `IsRectNull`不同，后者确定矩形的所有坐标是否为零。

> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>  CRect::IsRectNull

确定 `CRect` 的上、左、下、右值是否都等于0。

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>返回值

如果 `CRect`的上、左、下、右值都等于0，则为非零值;否则为0。

### <a name="remarks"></a>备注

与 `IsRectEmpty`不同，后者确定矩形是否为空。

### <a name="example"></a>示例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

##  <a name="movetox"></a>  CRect::MoveToX

调用此函数可将矩形移动到*x*指定的绝对 x 坐标。

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
矩形左上角的绝对 x 坐标。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>  CRect::MoveToXY

调用此函数可将矩形移动到指定的绝对 x 和 y 坐标。

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
矩形左上角的绝对 x 坐标。

*y*<br/>
矩形左上角的绝对 y 坐标。

*point*<br/>
指定矩形左上角的 `POINT` 结构。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>  CRect::MoveToY

调用此函数可将矩形移动到由*y*指定的绝对 y 坐标。

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>参数

*y*<br/>
矩形左上角的绝对 y 坐标。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>  CRect::NormalizeRect

规范化 `CRect` 以便高度和宽度均为正值。

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>备注

该矩形针对第四象限定位进行标准化，Windows 通常使用该坐标进行坐标。 `NormalizeRect` 比较上限值和下限值，如果顶部大于底部，则交换它们。 同样，如果左侧大于右侧值，它将交换左侧值和右侧值。 当处理不同的映射模式和反转矩形时，此函数很有用。

> [!NOTE]
> 以下 `CRect` 成员函数需要规范化矩形才能正常工作： [Height](#height)、 [Width](#width)、 [Size](#size)、 [IsRectEmpty](#isrectempty)、 [PtInRect](#ptinrect)、 [EqualRect](#equalrect)、 [UnionRect](#unionrect)、 [IntersectRect](#intersectrect)、 [SubtractRect](#subtractrect)、 [operator = =](#operator_eq_eq)、 [operator！ =](#operator_neq)、 [operator &#124; ](#operator_or)、 [operator &#124;=](#operator_or_eq)、 [operator &](#operator_amp)和[运算符 & =](#operator_amp_eq)。

### <a name="example"></a>示例

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>  CRect::OffsetRect

按指定的偏移量移动 `CRect`。

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
指定向左或向右移动的量。 它必须为负数才能向左移动。

*y*<br/>
指定向上或向下移动的量。 必须为负数才能向上移动。

*point*<br/>
包含一个[点](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象，该对象指定要移动的维度。

*size*<br/>
包含一个[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](csize-class.md)对象，用于指定要移动的维度。

### <a name="remarks"></a>备注

沿 x*轴和 y 轴沿 y 轴*移动 `CRect`*x*单位。 *X*和*y*参数是有符号值，因此 `CRect` 可以向左或向右移动或向下移动。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect：： operator LPCRECT 将 `CRect` 转换为[LPCRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>备注

使用此函数时，不需要地址（ **&** ）运算符。 将 `CRect` 对象传递到需要 `LPCRECT`的函数时，将自动使用此运算符。

##  <a name="operator_lprect"></a>CRect：： operator LPRECT

将`CRect`转换为 [LPRECT](../../mfc/reference/data-types-mfc.md)   。

```
operator LPRECT() throw();
```

### <a name="remarks"></a>备注

使用此函数时，不需要地址（ **&** ）运算符。 将 `CRect` 对象传递到需要 `LPRECT`的函数时，将自动使用此运算符。

### <a name="example"></a>示例

请参阅[CRect：： OPERATOR LPCRECT](#operator_lpcrect)的示例。

##  <a name="operator_eq"></a>CRect：： operator =

将*srcRect*分配给 `CRect`。

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>参数

*srcRect*<br/>
引用源矩形。 可以是[矩形](/windows/win32/api/windef/ns-windef-rect)或 `CRect`。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect：： operator = =

通过比较左上角和右下角的坐标，确定 `rect` 是否等于 `CRect`。

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>参数

*rect*<br/>
引用源矩形。 可以是[矩形](/windows/win32/api/windef/ns-windef-rect)或 `CRect`。

### <a name="return-value"></a>返回值

如果相等，则为非零值;否则为0。

### <a name="remarks"></a>备注

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

##  <a name="operator_neq"></a>CRect：： operator！ =

通过比较左上角和右下角的坐标，确定*rect*是否不等于 `CRect`。

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>参数

*rect*<br/>
引用源矩形。 可以是[矩形](/windows/win32/api/windef/ns-windef-rect)或 `CRect`。

### <a name="return-value"></a>返回值

如果不等于，则为非零;否则为0。

### <a name="remarks"></a>备注

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

##  <a name="operator_add_eq"></a>CRect：： operator + =

前两个重载按指定的偏移量 `CRect` 移动。

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>参数

*point*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象，指定矩形要移动的单位数。

*size*<br/>
[SIZE](/windows/win32/api/windef/ns-windef-size) Structure 或[CSize](csize-class.md)对象，用于指定要将矩形移动的单位数。

*lpRect*<br/>
指向一个[RECT](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect` 对象，该对象包含 `CRect`的每一侧的单位数。

### <a name="remarks"></a>备注

参数的*x*和*y* （或 `cx` 和 `cy`）值将添加到 `CRect`中。

第三个重载增加 `CRect` 参数的每个成员中指定的单位数。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect：： operator-=

前两个重载按指定的偏移量 `CRect` 移动。

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>参数

*point*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象，指定矩形要移动的单位数。

*size*<br/>
[SIZE](/windows/win32/api/windef/ns-windef-size) Structure 或[CSize](csize-class.md)对象，用于指定要将矩形移动的单位数。

*lpRect*<br/>
指向一个[RECT](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect` 对象，该对象包含要在 `CRect`的每一侧 deflate 的单位数。

### <a name="remarks"></a>备注

参数的*x*和*y* （或 `cx` 和 `cy`）值是从 `CRect`中减去的。

第三个重载压缩 `CRect` 参数的每个成员中指定的单位数。 请注意，此重载的作用类似于[DeflateRect](#deflaterect)。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect：： operator &amp;=

将 `CRect` 等于 `CRect` 和 `rect`的交集。

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>参数

*rect*<br/>
包含[矩形](/windows/win32/api/windef/ns-windef-rect)或 `CRect`。

### <a name="remarks"></a>备注

交集是两个矩形中包含的最大矩形。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

请参阅[CRect：： IntersectRect](#intersectrect)的示例。

##  <a name="operator_or_eq"></a>CRect：： operator &#124;=

将 `CRect` 等于 `CRect` 和 `rect`的并集。

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>参数

*rect*<br/>
包含 `CRect` 或[RECT](/windows/win32/api/windef/ns-windef-rect)。

### <a name="remarks"></a>备注

联合是包含两个源矩形的最小矩形。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect：： operator +

前两个重载返回一个 `CRect` 对象，该对象等于由指定偏移量替换的 `CRect`。

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>参数

*point*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象，用于指定要将返回值移动到的单位数。

*size*<br/>
[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](csize-class.md)对象，用于指定要将返回值移动到的单位数。

*lpRect*<br/>
指向一个[RECT](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect` 对象，该对象包含要在返回值的每一侧的单位数。

### <a name="return-value"></a>返回值

`CRect` 按照参数中指定的单位数 `CRect` 移动或因为这样做。

### <a name="remarks"></a>备注

参数的*x*和*y* （或 `cx` 和 `cy`）参数将添加到 `CRect`的位置。

第三个重载返回一个新的 `CRect`，该等于按参数的每个成员中指定的单位数放大 `CRect`。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect：： operator-

前两个重载返回一个 `CRect` 对象，该对象等于由指定偏移量替换的 `CRect`。

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>参数

*point*<br/>
一个[点](/windows/win32/api/windef/ns-windef-point)结构或 `CPoint` 对象，它指定要将返回值移动到的单位数。

*size*<br/>
一个[大小](/windows/win32/api/windef/ns-windef-size)结构或 `CSize` 对象，它指定返回值要移动的单位数。

*lpRect*<br/>
指向一个[RECT](/windows/win32/api/windef/ns-windef-rect)结构或 `CRect` 对象，该对象包含 deflate 返回值每一侧的单位数。

### <a name="return-value"></a>返回值

`CRect` 按照参数中指定的单位数 `CRect` 移动或 deflating。

### <a name="remarks"></a>备注

参数的*x*和*y* （或 `cx` 和 `cy`）参数从 `CRect`的位置中减去。

第三个重载返回一个新的 `CRect`，它等于 `CRect` 伸缩按参数的每个成员中指定的单位数。 请注意，此重载的作用类似于[DeflateRect](#deflaterect)，而不是[SubtractRect](#subtractrect)。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect：： operator &amp;

返回 `CRect`，它是 `CRect` 和*rect2*的交集。

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>参数

*rect2*<br/>
包含[矩形](/windows/win32/api/windef/ns-windef-rect)或 `CRect`。

### <a name="return-value"></a>返回值

一个 `CRect`，它是 `CRect` 和*rect2*的交集。

### <a name="remarks"></a>备注

交集是两个矩形中包含的最大矩形。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>  CRect::operator &#124;

返回 `CRect`，它是 `CRect` 和*rect2*的联合。

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>参数

*rect2*<br/>
包含[矩形](/windows/win32/api/windef/ns-windef-rect)或 `CRect`。

### <a name="return-value"></a>返回值

一个 `CRect`，它是 `CRect` 和*rect2*的联合。

### <a name="remarks"></a>备注

联合是包含两个矩形的最小矩形。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>  CRect::PtInRect

确定指定点是否位于 `CRect`中。

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>参数

*point*<br/>
包含[点](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象。

### <a name="return-value"></a>返回值

如果点位于 `CRect`中，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果某个点位于左侧或顶部，或者位于所有四个侧，则该点位于 `CRect` 内。 右侧或底部的点位于 `CRect`之外。

> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

##  <a name="setrect"></a>  CRect::SetRect

将 `CRect` 的尺寸设置为指定坐标。

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>参数

*x1*<br/>
指定左上角的 x 坐标。

*y1*<br/>
指定左上角的 y 坐标。

*x2*<br/>
指定右下角的 x 坐标。

*y2*<br/>
指定右下角的 y 坐标。

### <a name="example"></a>示例

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect：： SetRectEmpty

通过将所有坐标设置为零，使 `CRect` 空矩形。

```
void SetRectEmpty() throw();
```

### <a name="example"></a>示例

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

##  <a name="size"></a>CRect：： SIZE

返回值的 `cx` 和 `cy` 成员包含 `CRect`的高度和宽度。

```
CSize Size() const throw();
```

### <a name="return-value"></a>返回值

一个包含`CRect`大小的[CSize](csize-class.md) 对象。

### <a name="remarks"></a>备注

高度或宽度可以为负数。

> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>  CRect::SubtractRect

使 `CRect` 的尺寸等于 `lpRectSrc2` 从 `lpRectSrc1`中减去。

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>参数

*lpRectSrc1*<br/>
指向要从中减去矩形的 [RECT](/windows/win32/api/windef/ns-windef-rect) 结构或`CRect`对象。

*lpRectSrc2*<br/>
指向要从*lpRectSrc1*参数指向的矩形中减去 `RECT` 结构或 `CRect` 对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

该减法是包含*lpRectScr1*中不在*lpRectScr1*和*lpRectScr2*交集内的所有点的最小矩形。

如果*lpRectSrc2*指定的矩形未完全重叠*lpRectSrc1*至少一个 x 或 y 方向中指定的矩形，则*lpRectSrc1*指定的矩形将保持不变。

例如，如果*lpRectSrc1*为（10，10，100100）， *lpRectSrc2*为（50，50，150150），则当函数返回时，由*lpRectSrc1*指向的矩形将保持不变。 但是，如果*lpRectSrc1*为（10，10，100100），而*lpRectSrc2*为（50，10，150150），则*lpRectSrc1*指向的矩形将包含该函数返回时的坐标（10，10，50100）。

`SubtractRect` 不同于[operator-](#operator_-)或[operator-=](#operator_-_eq)。 这些运算符都不会调用 `SubtractRect`。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

##  <a name="topleft"></a>  CRect::TopLeft

坐标作为对 `CRect`中所包含的[CPoint](cpoint-class.md)对象的引用返回。

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>返回值

矩形左上角的坐标。

### <a name="remarks"></a>备注

您可以使用此函数获取或设置矩形的左上角。 通过在赋值运算符的左侧使用此函数设置角。

### <a name="example"></a>示例

请参阅[CRect：： CenterPoint](#centerpoint)的示例。

##  <a name="unionrect"></a>  CRect::UnionRect

使 `CRect` 的尺寸等于两个源矩形的并集。

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>参数

*lpRect1*<br/>
指向包含源矩形的 [RECT](/windows/win32/api/windef/ns-windef-rect) 或`CRect`。

*lpRect2*<br/>
指向包含源矩形的 `RECT` 或 `CRect`。

### <a name="return-value"></a>返回值

如果联合不为空，则为非零值;如果联合为空，则为0。

### <a name="remarks"></a>备注

联合是包含两个源矩形的最小矩形。

Windows 忽略空矩形的尺寸;也就是说，没有高度或没有宽度的矩形。

> [!NOTE]
>  两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect：： Width

通过从适当的值中减去左值来计算 `CRect` 的宽度。

```
int Width() const throw();
```

### <a name="return-value"></a>返回值

`CRect`的宽度。

### <a name="remarks"></a>备注

宽度可以为负数。

> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>另请参阅

[CPoint 类](cpoint-class.md)<br/>
[CSize 类](csize-class.md)<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)
