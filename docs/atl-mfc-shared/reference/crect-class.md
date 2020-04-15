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
ms.openlocfilehash: c59ed587e2c8e51f5c08a026a7ee0b9d0af25168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317704"
---
# <a name="crect-class"></a>CRect 类

类似于 Windows [RECT](/windows/win32/api/windef/ns-windef-rect)结构。

## <a name="syntax"></a>语法

```
class CRect : public tagRECT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CRect：CRect](#crect)|构造 `CRect` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRect：：右下](#bottomright)|返回 的右下角点`CRect`。|
|[CRect：：中心点](#centerpoint)|返回 的中心`CRect`点。|
|[CRect：：复制](#copyrect)|将源矩形的尺寸复制到`CRect`。|
|[CRect：:D](#deflaterect)|减小 的`CRect`宽度和高度。|
|[CRect：：平等](#equalrect)|确定是否`CRect`等于给定的矩形。|
|[CRect：：高度](#height)|计算 的高度`CRect`。|
|[CRect：：充气](#inflaterect)|增加 的`CRect`宽度和高度。|
|[CRect：：相交雷](#intersectrect)|设置`CRect`等于两个矩形的交集。|
|[CRect：：isrectEmpty](#isrectempty)|确定是否`CRect`为空。 `CRect`如果宽度和/或高度为 0，则为空。|
|[CRect：：IsrectNull](#isrectnull)|确定`top`、 `bottom`、`left`和`right`成员变量是否都等于 0。|
|[Crect：：移动](#movetox)|移动到`CRect`指定的 x 坐标。|
|[Crect：：移动](#movetoxy)|移动到`CRect`指定的 x 坐标和 y 坐标。|
|[Crect：：移动玩具](#movetoy)|移动到`CRect`指定的 y 坐标。|
|[CRect：：规范化Rect](#normalizerect)|标准化 的高度`CRect`和宽度。|
|[CRect：：偏移重](#offsetrect)|按`CRect`指定的偏移量移动。|
|[Crect：:P](#ptinrect)|确定指定的点是否位于 中`CRect`。|
|[CRect：：SetRect](#setrect)|设置 的`CRect`尺寸。|
|[CRect：：设置重新清空](#setrectempty)|设置`CRect`为空矩形（所有坐标等于 0）。|
|[CRect：：大小](#size)|计算 的大小`CRect`。|
|[CRect：：减法](#subtractrect)|从另一个矩形中减去一个矩形。|
|[CRect：左上](#topleft)|返回 的左上角点`CRect`。|
|[CRect：：联合](#unionrect)|设置`CRect`等于两个矩形的合并。|
|[CRect：：宽度](#width)|计算 的`CRect`宽度。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CRect：：运算符 -](#operator_-)|从`CRect`中减去给定的偏移量或放`CRect`空并返回生成的`CRect`。|
|[CRect：：操作员LPCRECT](#operator_lpcrect)|将 `CRect` 转换为 `LPCRECT`。|
|[CRect：：操作员 LPRECT](#operator_lprect)|将 `CRect` 转换为 `LPRECT`。|
|[CRect：：操作员！*](#operator_neq)|确定是否`CRect`不等于矩形。|
|[CRect：：运算符&amp;](#operator_amp)|创建 和`CRect`的交集，并返回生成的`CRect`。|
|[CRect：：运算符&amp;=](#operator_amp_eq)|设置`CRect`等于 和 的`CRect`交集和矩形。|
|[CRect：：操作员&#124;](#operator_or)|创建 和`CRect`的联合矩形，并返回生成的`CRect`。|
|[CRect：：操作员&#124;|](#operator_or_eq)|设置`CRect`等于 和 的`CRect`合并。|
|[CRect：：运算符 |](#operator_add)|将给定偏移量添加到`CRect`或膨胀`CRect`并返回生成的`CRect`。|
|[CRect：：操作员 |](#operator_add_eq)|将指定的偏移量添加到`CRect`或膨胀 。 `CRect`|
|[CRect：：运算符 |](#operator_eq)|将矩形的尺寸复制到`CRect`。|
|[CRect：：运算符 -*](#operator_-_eq)|从`CRect`中减去指定的偏移量或放空`CRect`。|
|[CRect：：运算符 |](#operator_eq_eq)|确定是否`CRect`等于矩形。|

## <a name="remarks"></a>备注

`CRect`还包括用于操作`CRect`对象和 Windows`RECT`结构的成员函数。

对象`CRect`可以在`RECT`结构的任何位置作为函数参数传递，`LPCRECT`也可以`LPRECT`传递 。

> [!NOTE]
> 此类派生自结构`tagRECT`。 （名称`tagRECT`是`RECT`结构不太常用的名称。这意味着`top``right``bottom``left``RECT`结构的数据成员 （、 、 和 ） 是 可`CRect`访问的数据成员。

包含`CRect`定义矩形的左上角和右下角点的成员变量。

指定`CRect`时，必须小心构造它，以便将其规范化 — 换句话说，左坐标的值小于右侧，顶部小于底部。 例如，左上角（10，10）和右下角（20，20）定义一个规范化矩形，但左上角 （20，20） 和右下角 （10，10） 定义非规范化矩形。 如果矩形未规范化，许多`CRect`成员函数可能会返回不正确的结果。 （请参阅[CRect：：规范化 Rect，](#normalizerect)了解这些函数的列表。在调用需要规范化矩形的函数之前，可以通过调用`NormalizeRect`函数来规范化非规范化矩形。

使用`CRect`[CDC：:DPtoLP](../../mfc/reference/cdc-class.md#dptolp)和[CDC：：LPtoDP](../../mfc/reference/cdc-class.md#lptodp)成员函数操作 时，应谨慎。 如果显示上下文的映射模式使 y 范围为负，如 在 中`MM_LOENGLISH`，则`CDC::DPtoLP`将转换 ，`CRect`以便其顶部大于底部。 等`Height`函数`Size`随后将返回转换`CRect`高度的负值，矩形将非规范化。

使用重载`CRect`运算符时，第一个`CRect`操作数必须是 ;第二个可以是[RECT](/windows/win32/api/windef/ns-windef-rect)结构或`CRect`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagRECT`

`CRect`

## <a name="requirements"></a>要求

**标题：** atltype.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect：：右下

坐标将作为对 中包含的[CPoint](cpoint-class.md)对象的引用返回`CRect`。

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>返回值

矩形右下角的坐标。

### <a name="remarks"></a>备注

您可以使用此函数获取或设置矩形的右下角。 使用赋值运算符左侧的函数设置角。

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

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect：：中心点

通过添加左值和右`CRect`值并将之除以 2 以及添加顶部和底部值以及除以 2 来计算 的中心点。

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>返回值

作为`CPoint`的中心点的对象`CRect`。

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

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect：：复制

将`lpSrcRect`矩形复制到`CRect`中。

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>参数

*lpSrcrect*<br/>
指向要复制的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或`CRect`对象。

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

## <a name="crectcrect"></a><a name="crect"></a>CRect：CRect

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

*我*<br/>
指定 的`CRect`左位置。

*t*<br/>
指定 的顶部`CRect`。

*R*<br/>
指定 的正确位置`CRect`。

*B*<br/>
指定 的底部`CRect`。

*斯克拉特*<br/>
指具有 坐标的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*lpSrcrect*<br/>
指向`RECT`具有 坐标的结构`CRect`。

*点*<br/>
指定要构造的矩形的原点。 对应于左上角。

*大小*<br/>
指定要构造的矩形从左上角到右下角的位移。

*topLeft*<br/>
指定 的左上角位置`CRect`。

*bottomRight*<br/>
指定 的右下角位置`CRect`。

### <a name="remarks"></a>备注

如果未`left`给出参数，则不会初始化`top` `right`、和`bottom`成员。

`CRect`（`const RECT&`）`CRect`和`LPCRECT`（ ） 构造函数执行[复制重新 。](#copyrect) 其他构造函数直接初始化对象的成员变量。

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

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect：:D

`DeflateRect``CRect`通过移动其两侧向其中心。

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>参数

** x <br/>
指定要放气 的左侧和右侧的单位`CRect`数。

*Y*<br/>
指定要放气 的上部和下部的单位`CRect`数。

*大小*<br/>
指定要放放`CRect`的单位数[的大小或](/windows/win32/api/windef/ns-windef-size)[大小。](csize-class.md) 该`cx`值指定用于放气左右两侧的单位数，`cy`该值指定用于放气顶部和底部的单位数。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或`CRect`指定要放气每侧的单位数。

*我*<br/>
指定要放气 的左侧的单位`CRect`数。

*t*<br/>
指定要放气 顶部的单位`CRect`数。

*R*<br/>
指定要放气 右侧的单位`CRect`数。

*B*<br/>
指定要放气 的单位`CRect`数。

### <a name="remarks"></a>备注

为此，在`DeflateRect`左侧和顶部添加单位，并从右侧和底部减去单位。 的`DeflateRect`参数是已签名的值;正值放空`CRect`，负值膨胀。

前两个重载将两对相反的两对`CRect`放气，使其总宽度减少 2 倍*x* `cx`（或 ）， 其总高度减少 2`cy`倍*y* （或 ）。 其他两个重载使每一侧`CRect`都独立于其他侧进行放气。

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

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect：：平等

确定是否`CRect`等于给定的矩形。

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向包含矩形的左上角`CRect`和右下角坐标的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或对象。

### <a name="return-value"></a>返回值

如果两个矩形具有相同的顶部、左侧、底部和右侧值，则非零;否则 0。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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

## <a name="crectheight"></a><a name="height"></a>CRect：：高度

通过从底部值中`CRect`减去最高值来计算 的高度。

```
int Height() const throw();
```

### <a name="return-value"></a>返回值

的高度`CRect`。

### <a name="remarks"></a>备注

生成的值可以是负数。

> [!NOTE]
> 矩形必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect：：充气

`InflateRect`通过将其侧面`CRect`从中心移开而膨胀。

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>参数

** x <br/>
指定要膨胀 的左侧和右侧的单位`CRect`数。

*Y*<br/>
指定要膨胀 的上部和底部的单位`CRect`数。

*大小*<br/>
指定要膨胀的单位数的[SIZE](/windows/win32/api/windef/ns-windef-size)或`CRect`[CSize。](csize-class.md) 该`cx`值指定要膨胀左右两侧的单位数，`cy`该值指定要膨胀顶部和底部的单位数。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或`CRect`指定要膨胀每侧的单位数。

*我*<br/>
指定要膨胀 的单位`CRect`数。

*t*<br/>
指定要膨胀 的单位`CRect`数。

*R*<br/>
指定要膨胀 的右侧的单位`CRect`数。

*B*<br/>
指定要膨胀 的单位`CRect`数。

### <a name="remarks"></a>备注

为此，`InflateRect`从左侧和顶部减去单位，并在右侧和底部添加单位。 的`InflateRect`参数是已签名的值;正值膨胀`CRect`，负值将其放气。

前两个重载将两对相反的两对膨胀，`CRect`使其总宽度增加 2 倍*x* （或`cx`）， 其总高度增加 2*y*倍 y `cy`（或 ）。 其他两个重载使每一侧`CRect`相互膨胀，而与其他重载无关。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect：：相交雷

使等于`CRect`两个现有矩形的交集。

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>参数

*lpRect1*<br/>
指向包含源矩形的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或`CRect`对象。

*lpRect2*<br/>
指向包含源`RECT`矩形的结构`CRect`或对象。

### <a name="return-value"></a>返回值

如果交点不为空，则非零;如果交点为空，则为 0。

### <a name="remarks"></a>备注

交集是两个现有矩形中包含的最大矩形。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect：：isrectEmpty

确定是否`CRect`为空。

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>返回值

非零（`CRect`如果为空）;0，`CRect`如果不是空。

### <a name="remarks"></a>备注

如果宽度和/或高度为 0 或负，则矩形为空。 与`IsRectNull`不同，后者确定矩形的所有坐标是否为零。

> [!NOTE]
> 矩形必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect：：IsrectNull

确定 的`CRect`上值、左值、下值和右值是否都等于 0。

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>返回值

如果"的顶部`CRect`、左侧、底部和右侧"值都等于 0，则非零;如果"上、左、下和右"值均等于 0;如果"上、左、下和右"值均等于 0，则为非零。否则 0。

### <a name="remarks"></a>备注

与`IsRectEmpty`不同，后者确定矩形是否为空。

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

## <a name="crectmovetox"></a><a name="movetox"></a>Crect：：移动

调用此函数以将矩形移动到*x*指定的绝对 x 坐标。

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>参数

** x <br/>
矩形左上角的绝对 x 坐标。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>Crect：：移动

调用此函数以将矩形移动到指定的绝对 x 坐标和 y 坐标。

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>参数

** x <br/>
矩形左上角的绝对 x 坐标。

*Y*<br/>
矩形左上角的绝对 y 坐标。

*点*<br/>
指定`POINT`矩形的绝对左上角的结构。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>Crect：：移动玩具

调用此函数以将矩形移动到*y*指定的绝对 y 坐标。

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>参数

*Y*<br/>
矩形左上角的绝对 y 坐标。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect：：规范化Rect

规范化`CRect`，以便高度和宽度均为正数。

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>备注

矩形规范化为第四象限定位，Windows 通常用于坐标。 `NormalizeRect`比较顶部和底部值，如果顶部大于底部，则交换它们。 同样，如果左侧大于右侧，则交换左侧和右侧值。 在处理不同的映射模式和反转矩形时，此功能非常有用。

> [!NOTE]
> 以下`CRect`成员函数需要规范化矩形才能正常工作：[高度](#height)、[宽度](#width)、[大小](#size)[、isrectEmpty、PtInRect、](#isrectempty)[相等重、](#equalrect)[联合重整](#unionrect)、[相交雷ct、](#intersectrect)[减法、](#subtractrect)[运算符 *、](#operator_eq_eq)[操作员 ！*、](#operator_neq)[操作员&#124;、](#operator_or)[操作员&#124;、](#operator_or_eq)[操作员&](#operator_amp)和[运算符&=](#operator_amp_eq)。 [PtInRect](#ptinrect)

### <a name="example"></a>示例

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect：：偏移重

按`CRect`指定的偏移量移动。

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>参数

** x <br/>
指定向左或向右移动的金额。 向左移动必须为负数。

*Y*<br/>
指定向上或向下移动的金额。 向上移动必须为负数。

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象，指定要移动的两个维度。

*大小*<br/>
包含指定要移动的两个维度[的 SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](csize-class.md)对象。

### <a name="remarks"></a>备注

沿`CRect`x 轴和*y*单位沿 y 轴移动*x*单位。 *x*和*y*参数是签名值，`CRect`因此可以向左或向右移动，向上或向下移动。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect：：运算符 LPCRECT 将`CRect`转换为[LPCRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>备注

使用此函数时，不需要 地址**&**（ ） 运算符。 当您将`CRect`对象传递给需要 的`LPCRECT`函数时，将自动使用此运算符。

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect：：操作员 LPRECT

将 转换为`CRect` [LPRECT](../../mfc/reference/data-types-mfc.md)。

```
operator LPRECT() throw();
```

### <a name="remarks"></a>备注

使用此函数时，不需要 地址**&**（ ） 运算符。 当您将`CRect`对象传递给需要 的`LPRECT`函数时，将自动使用此运算符。

### <a name="example"></a>示例

请参阅[CRect：：运算符 LPCRECT](#operator_lpcrect)的示例。

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect：：运算符 |

将*srcRect* `CRect`分配给 。

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>参数

*斯克拉特*<br/>
引用源矩形。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="example"></a>示例

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect：：运算符 |

通过比较`rect`其左上角和右下角角的坐标，确定是否等于。 `CRect`

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>参数

*矩形*<br/>
引用源矩形。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>返回值

等于非零;否则 0。

### <a name="remarks"></a>备注

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect：：操作员！*

通过比较右上角和右下角的坐标，确定*整流*是否等于。 `CRect`

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>参数

*矩形*<br/>
引用源矩形。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>返回值

非零，如果不是相等;否则 0。

### <a name="remarks"></a>备注

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect：：操作员 |

前两个重载按`CRect`指定的偏移量移动。

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>参数

*点*<br/>
指定要移动矩形的单位数的[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象。

*大小*<br/>
指定要移动矩形的单位数的[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](csize-class.md)对象。

*lpRect*<br/>
指向包含要膨胀的两侧的`CRect`单位数的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)结构或对象。

### <a name="remarks"></a>备注

参数的*x*和*y* `cx` （`cy`或 和 ）`CRect`值将添加到 中。

第三个过载按`CRect`参数的每个成员中指定的单位数膨胀。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect：：运算符 -*

前两个重载按`CRect`指定的偏移量移动。

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>参数

*点*<br/>
指定要移动矩形的单位数的[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象。

*大小*<br/>
指定要移动矩形的单位数的[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](csize-class.md)对象。

*lpRect*<br/>
指向包含要放气 的每`CRect`一侧的单位数的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)结构或对象。

### <a name="remarks"></a>备注

参数的*x*和*y* `cx` （`cy`或 和 ）`CRect`值从 中减去。

第三个过载`CRect`按参数的每个成员中指定的单位数进行放量。 请注意，此重载函数类似于[DeflateRect](#deflaterect)。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect：：运算符&amp;=

设置`CRect`等于 和`rect`的`CRect`交集。

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>参数

*矩形*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="remarks"></a>备注

交集是两个矩形中包含的最大矩形。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

请参阅[CRect：：相交雷ct的示例](#intersectrect)。

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect：：操作员&#124;|

集`CRect`等于 和`rect`的`CRect`联合。

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>参数

*矩形*<br/>
包含 或`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)。

### <a name="remarks"></a>备注

联合是包含两个源矩形的最小矩形。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect：：运算符 |

前两个重载返回一`CRect`个对象，该对象`CRect`等于由指定的偏移量置换。

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>参数

*点*<br/>
指定要移动返回值的单位数的[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象。

*大小*<br/>
指定要移动返回值的单位数的[SIZE](/windows/win32/api/windef/ns-windef-size)结构或[CSize](csize-class.md)对象。

*lpRect*<br/>
指向包含要膨胀返回值每`CRect`一侧的单位数的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或对象。

### <a name="return-value"></a>返回值

由按参数中指定的单位数移动或膨胀`CRect`的结果。 `CRect`

### <a name="remarks"></a>备注

参数的*x*和*y* `cx` （`cy`或 和 ）`CRect`参数将添加到位置。

第三个重载返回`CRect`一个新值，`CRect`该新重载等于按参数的每个成员中指定的单位数膨胀。

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect：：运算符 -

前两个重载返回一`CRect`个对象，该对象`CRect`等于由指定的偏移量置换。

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>参数

*点*<br/>
指定[POINT](/windows/win32/api/windef/ns-windef-point)要移动返回`CPoint`值的单位数的 POINT 结构或对象。

*大小*<br/>
指定[SIZE](/windows/win32/api/windef/ns-windef-size)要移动返回`CSize`值的单位数的 SIZE 结构或对象。

*lpRect*<br/>
指向包含用于放气返回值`CRect`每一侧的单位数的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或对象。

### <a name="return-value"></a>返回值

由按参数中指定的单位数移动或消减`CRect`的结果。 `CRect`

### <a name="remarks"></a>备注

参数的*x*和*y* `cx` （`cy`或 和 ） 参数`CRect`从 位置中减去。

第三个重载返回`CRect`一个新值，`CRect`该新重载等于按参数的每个成员中指定的单位数进行放气。 请注意，此重载函数如[DeflateRect，](#deflaterect)而不是[减减 。](#subtractrect)

### <a name="example"></a>示例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect：：运算符&amp;

返回`CRect`作为 和`CRect`*rect2*的交集的 。

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>参数

*rect2*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>返回值

A`CRect`是 和`CRect`*rect2*的交集。

### <a name="remarks"></a>备注

交集是两个矩形中包含的最大矩形。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect：：操作员&#124;

返回`CRect`和 的 联合`CRect`项 *。*

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>参数

*rect2*<br/>
包含[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`。

### <a name="return-value"></a>返回值

A`CRect`是 和`CRect`*rect2*的合并。

### <a name="remarks"></a>备注

联合是包含两个矩形的最小矩形。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a>Crect：:P

确定指定的点是否位于 中`CRect`。

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>参数

*点*<br/>
包含[POINT](/windows/win32/api/windef/ns-windef-point)结构或[CPoint](cpoint-class.md)对象。

### <a name="return-value"></a>返回值

如果点位于 中`CRect`，则非零。否则 0。

### <a name="remarks"></a>备注

如果点位于左侧`CRect`或顶部或位于所有四面内，则该点位于内。 右侧或底部的点位于外部`CRect`。

> [!NOTE]
> 矩形必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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

## <a name="crectsetrect"></a><a name="setrect"></a>CRect：：SetRect

将 的`CRect`尺寸设置到指定的坐标。

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

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect：：设置重新清空

通过将`CRect`所有坐标设置为零，使矩形变为空矩形。

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

## <a name="crectsize"></a><a name="size"></a>CRect：：大小

返回`cx`值`cy`和 成员包含`CRect`的高度和宽度。

```
CSize Size() const throw();
```

### <a name="return-value"></a>返回值

包含 大小的[CSize](csize-class.md)对象`CRect`。

### <a name="remarks"></a>备注

高度或宽度可以是负数。

> [!NOTE]
> 矩形必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect：：减法

使 的`CRect`尺寸等于 从`lpRectSrc2``lpRectSrc1`的减法。

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>参数

*lpRectSrc1*<br/>
指向要从中减去矩形的`CRect` [RECT](/windows/win32/api/windef/ns-windef-rect)结构或对象。

*lprectSrc2*<br/>
指向要从`RECT` `CRect` *lpRectSrc1*参数指向的矩形中减去的结构或对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

减法是最小的矩形，它包含*lpRectScr1*中所有不在*lpRectScr1 和 lpRectScr2*的*lpRectScr2*交集中的点。

如果*lpRectSrc2*指定的矩形不完全重叠*lpRectSrc1*指定的矩形，则*lpRectSrc1*指定的矩形将至少与一个 x 或 y 方向重叠，则该矩形将保持不变。

例如，如果*lpRectSrc1*为 （10，10， 100，100）和*lpRectSrc2* （50，50， 150，150），则当函数返回时 *，lpRectSrc1*指向的矩形将保持不变。 但是 *，如果 lpRectSrc1* （10，10， 100，100） 和*lpRectSrc2*是 （50，10， 150，150），则在函数返回时 *，lpRectSrc1*指向的矩形将包含坐标 （10，10，50，100）。

`SubtractRect`与[运算符和运算符](#operator_-) [-=](#operator_-_eq)不同。 这两个运营商都没有打过`SubtractRect`电话。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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

## <a name="crecttopleft"></a><a name="topleft"></a>CRect：左上

坐标将作为对 中包含的[CPoint](cpoint-class.md)对象的引用返回`CRect`。

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>返回值

矩形左上角的坐标。

### <a name="remarks"></a>备注

可以使用此函数获取或设置矩形的左上角。 使用赋值运算符左侧的函数设置角。

### <a name="example"></a>示例

请参阅[CRect：：中心点](#centerpoint)的示例。

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect：：联合

使的`CRect`尺寸等于两个源矩形的合并。

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>参数

*lpRect1*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)或`CRect`包含源矩形。

*lpRect2*<br/>
指向 包含`RECT`源`CRect`矩形的 或。

### <a name="return-value"></a>返回值

如果联合不为空，则为非零;如果联合为空，则为 0。

### <a name="remarks"></a>备注

联合是包含两个源矩形的最小矩形。

窗口忽略空矩形的尺寸;Windows 忽略空矩形的尺寸。即没有高度或没有宽度的矩形。

> [!NOTE]
> 两个矩形都必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

### <a name="example"></a>示例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a>CRect：：宽度

通过从右值中`CRect`减去左值来计算 的宽度。

```
int Width() const throw();
```

### <a name="return-value"></a>返回值

的宽度`CRect`。

### <a name="remarks"></a>备注

宽度可以是负数。

> [!NOTE]
> 矩形必须规范化，否则此函数可能会失败。 在调用此函数之前，可以调用[NormalizeRect](#normalizerect)来规范化矩形。

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
[矩形](/windows/win32/api/windef/ns-windef-rect)
