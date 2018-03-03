---
title: "CRect 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 067f683b5322b11a4ca33f015d64850c8113ce18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crect-class"></a>CRect 类
类似于 Windows [RECT](../../mfc/reference/rect-structure1.md)结构。  
  
## <a name="syntax"></a>语法  
  
```  
class CRect : public tagRECT  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRect::CRect](#crect)|构造 `CRect` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRect::BottomRight](#bottomright)|返回的右下角点`CRect`。|  
|[CRect::CenterPoint](#centerpoint)|返回的中心点`CRect`。|  
|[CRect::CopyRect](#copyrect)|将复制的源矩形的尺寸`CRect`。|  
|[CRect::DeflateRect](#deflaterect)|减少的宽度和高度`CRect`。|  
|[CRect::EqualRect](#equalrect)|确定是否`CRect`等于给定矩形。|  
|[CRect::Height](#height)|计算的高度`CRect`。|  
|[CRect::InflateRect](#inflaterect)|增加的宽度和高度`CRect`。|  
|[CRect::IntersectRect](#intersectrect)|集`CRect`等于两个矩形交集。|  
|[CRect::IsRectEmpty](#isrectempty)|确定是否`CRect`为空。 `CRect`如果，为空的宽度和/或高度均为 0。|  
|[CRect::IsRectNull](#isrectnull)|确定是否**顶部**，**底部**，**左**，和**右**成员变量在所有相等为 0。|  
|[CRect::MoveToX](#movetox)|将移动`CRect`到指定的 x 坐标。|  
|[CRect::MoveToXY](#movetoxy)|将移动`CRect`指定到 x 和 y 坐标。|  
|[CRect::MoveToY](#movetoy)|将移动`CRect`到指定的 y 坐标。|  
|[Crect:: Normalizerect](#normalizerect)|标准化的高度和宽度`CRect`。|  
|[CRect::OffsetRect](#offsetrect)|将移动`CRect`由指定的偏移量。|  
|[CRect::PtInRect](#ptinrect)|确定指定的点是否位于内`CRect`。|  
|[CRect::SetRect](#setrect)|设置的尺寸`CRect`。|  
|[CRect::SetRectEmpty](#setrectempty)|集`CRect`到空矩形 （所有坐标都等于 0）。|  
|[CRect::Size](#size)|计算的大小`CRect`。|  
|[CRect::SubtractRect](#subtractrect)|减去从另一个矩形。|  
|[CRect::TopLeft](#topleft)|返回的左上角点`CRect`。|  
|[CRect::UnionRect](#unionrect)|集`CRect`等于两个矩形的联合。|  
|[CRect::Width](#width)|计算的宽度`CRect`。|  
  
### <a name="public-operators"></a>公共运算符    
|名称|描述|  
|----------|-----------------|  
|[CRect::operator-](#operator_-)|减去从给定的偏移量`CRect`或压缩`CRect`，并返回结果`CRect`。|  
|[CRect::operator LPCRECT](#operator_lpcrect)|将转换`CRect`到**LPCRECT**。|  
|[CRect::operator LPRECT](#operator_lprect)|将转换`CRect`到`LPRECT`。|  
|[CRect::operator ！ =](#operator_neq)|确定是否`CRect`是否不等于矩形。|  
|[CRect::operator&amp;](#operator_amp)|创建的交集`CRect`和一个矩形，并返回结果`CRect`。|  
|[CRect::operator&amp;=](#operator_amp_eq)|集`CRect`相等的交集`CRect`和矩形。|  
|[CRect::operator |](#operator_or)|创建的联合`CRect`和一个矩形，并返回结果`CRect`。|  
|[CRect::operator |=](#operator_or_eq)|集`CRect`等于的联合`CRect`和矩形。|  
|[CRect::operator +](#operator_add)|将添加到给定的偏移量`CRect`或放大`CRect`，并返回结果`CRect`。|  
|[CRect::operator + =](#operator_add_eq)|将添加到指定的偏移量`CRect`或放大`CRect`。|  
|[CRect::operator =](#operator_eq)|将复制到的矩形的尺寸`CRect`。|  
|[CRect::operator =](#operator_-_eq)|减去指定的偏移量从`CRect`或压缩`CRect`。|  
|[CRect::operator = =](#operator_eq_eq)|确定是否`CRect`等同于一个矩形。|  
  
## <a name="remarks"></a>备注  
 `CRect`此外包括成员函数以操作`CRect`对象和 Windows`RECT`结构。  
  
 A`CRect`对象可以作为函数参数传递无论在何处`RECT`结构， **LPCRECT**，或`LPRECT`可以传递。  
  
> [!NOTE]
>  此类派生自**tagRECT**结构。 (名称**tagRECT**是较少通常使用名称`RECT`结构。)这意味着，数据成员 (**左**，**顶部**，**右**，和**底部**) 的`RECT`结构不是可访问的数据成员`CRect`。  
  
 A`CRect`包含定义的矩形的左上角和右下角的点的成员变量。  
  
 指定时`CRect`，您必须小心地将其构造它，以便它进行了规范化-换而言之，以便的左坐标值是否小于右侧和顶部小于底部。 例如，左上角的 (10,10) 和右下角 (20,20) 定义规范化的矩形，但左上角的 (20,20) 并右下方 (10,10) 定义非标准化的矩形。 如果在该矩形非标准化，许多`CRect`成员函数可能会返回不正确的结果。 (请参阅[crect:: Normalizerect](#normalizerect)有关这些函数的列表。)在调用某个函数需要规范化的矩形之前，你可以通过调用来进行规范化非标准化矩形`NormalizeRect`函数。  
  
 操作时要格外小心`CRect`与[CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp)和[CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp)成员函数。 如果显示上下文的映射模式会因此 y 范围为负，如`MM_LOENGLISH`，然后`CDC::DPtoLP`将转换`CRect`，以便其顶部大于底部。 函数如**高度**和**大小**然后将返回负数值的转换后的高度`CRect`，并且在该矩形将非规范化。  

  
 当使用重载`CRect`运算符，第一个操作数必须是`CRect`; 第二个可以是[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>惠?  
 **标头：** atltypes.h  
  
##  <a name="bottomright"></a>CRect::BottomRight  
 作为对引用返回坐标[CPoint](cpoint-class.md)中包含的对象`CRect`。  
  
```  
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```  
  
### <a name="return-value"></a>返回值  
 矩形右下角的坐标。  
  
### <a name="remarks"></a>备注  
 此函数可用于获取或设置矩形右下角。 通过在赋值运算符的左侧使用此函数中设置角。  
  
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
  
##  <a name="centerpoint"></a>CRect::CenterPoint 
 计算的中心点`CRect`通过添加左侧和右侧值和除以两个，并添加顶部和底部值除以两个。  
  
```  
CPoint CenterPoint() const throw();
```  
  
### <a name="return-value"></a>返回值  
 A`CPoint`对象，它的中心点`CRect`。  
  
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
  
##  <a name="copyrect"></a>CRect::CopyRect  
 副本`lpSrcRect`到矩形`CRect`。  
  
```  
void CopyRect(LPCRECT lpSrcRect) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lpSrcRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`要复制的对象。  
  
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

  
##  <a name="crect"></a>CRect::CRect  
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
 *l*  
 指定的左边的位置`CRect`。  
  
 *t*  
 指定的顶部`CRect`。  
  
 *r*  
 指定的正确位置`CRect`。  
  
 *b*  
 指定的底部`CRect`。  
  
 *srcRect*  
 是指[RECT](../../mfc/reference/rect-structure1.md)结构的坐标`CRect`。  
  
 `lpSrcRect`  
 指向`RECT`结构的坐标`CRect`。  
  
 `point`  
 指定要构造的矩形的起始点。 对应于左上角。  
  
 `size`  
 指定到右下角要构造的矩形的左上角的偏移。  
  
 *左边框*  
 指定的左上角位置`CRect`。  
  
 *bottomRight*  
 指定的右下角位置`CRect`。  
  
### <a name="remarks"></a>备注  
 如果未提供参数，**左**，**顶部**，**右**，和**底部**成员未初始化。  
  
 `CRect`(**Const RECT &**) 和`CRect`(**LPCRECT**) 构造函数执行[CopyRect](#copyrect)。 其他构造函数直接初始化的对象的成员变量。  
  
### <a name="example"></a>示例  
```cpp  
 // default constructor doesn't initialize!
 CRect rectUnknown;

 // four-integers are left, top, right, and bottom
 CRect rect(0, 0, 100, 50);
 ASSERT(rect.Width() == 100);
 ASSERT(rect.Height() == 50);

 // Initialize from RECT stucture
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
  
##  <a name="deflaterect"></a>CRect::DeflateRect  
 `DeflateRect`压缩`CRect`通过向其中心移动边。  
  
```  
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要 deflate 左侧的单位数和左右两边的`CRect`。  
  
 *y*  
 指定要 deflate 顶部和底部的单位数`CRect`。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)或[CSize](csize-class.md) ，它指定要 deflate 的单位数`CRect`。 `cx`值指定要 deflate 左侧和右侧的单元数量与`cy`值指定要 deflate 顶部和底部的单位数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`，它指定要 deflate 每一侧的单位数。  
  
 *l*  
 指定要 deflate 左侧的单位数`CRect`。  
  
 *t*  
 指定要 deflate 顶部的单位数`CRect`。  
  
 *r*  
 指定要 deflate 的右侧的单位数`CRect`。  
  
 *b*  
 指定要 deflate 底部的单位数`CRect`。  
  
### <a name="remarks"></a>备注  
 若要这样做，`DeflateRect`将单位添加到 left 和 top 和减去从右侧和底部的单位。 参数`DeflateRect`进行签名值; 正值 deflate`CRect`和负值放大量它。  
  
 前两个重载 deflate 这两个对的另一侧`CRect`，以便其总宽度降低两倍*x* (或`cx`) 和窗体的总高度减少两倍*y* (或`cy`)。 其他两个重载 deflate 的每一侧`CRect`相互独立地。  
  
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
  
##  <a name="equalrect"></a>CRect::EqualRect  
 确定是否`CRect`等于给定矩形。  
  
```  
BOOL EqualRect(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`包含一个矩形的左上角和右下角坐标的对象。  
  
### <a name="return-value"></a>返回值  
 如果两个矩形具有相同的顶部、 左侧、 底部，和右值; 则为非 0否则为 0。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
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

##  <a name="height"></a>CRect::Height  
 计算的高度`CRect`通过减去从最低值位于顶部的值。  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>返回值  
 高度`CRect`。  
  
### <a name="remarks"></a>备注  
 生成的值可以是负值。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(20, 30, 80, 70);
 int nHt = rect.Height();

```cpp  
   CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

   // nHt is now 40
   ASSERT(nHt == 40);   
```

  
##  <a name="inflaterect"></a>CRect::InflateRect  
 `InflateRect`放大`CRect`通过从其中心移动边。  
  
```  
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要放大量左侧的单位数和左右两边的`CRect`。  
  
 *y*  
 指定要放大量顶部和底部的单位数`CRect`。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)或[CSize](csize-class.md) ，它指定要放大量的单位数`CRect`。 `cx`值指定要放大量左侧和右侧的单元数量与`cy`值指定要放大量顶部和底部的单位数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`，它指定要放大量每一侧的单位数。  
  
 *l*  
 指定要放大量的左侧的单位数`CRect`。  
  
 *t*  
 指定要放大量顶部的单位数`CRect`。  
  
 *r*  
 指定要放大量的右侧的单位数`CRect`。  
  
 *b*  
 指定要放大量底部的单位数`CRect`。  
  
### <a name="remarks"></a>备注  
 若要这样做，`InflateRect`减去从 left 和 top 的单位并将设备添加到右侧和底部。 参数`InflateRect`进行签名值; 正值放大量`CRect`和负值 deflate 它。  
  
 前两个重载放大量这两个对的另一侧`CRect`以便其总宽度增加两倍*x* (或`cx`) 和窗体的总高度增加两倍*y* (或`cy`)。 其他两个重载放大量的每一侧`CRect`相互独立地。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(0, 0, 300, 300);
 rect.InflateRect(50, 200);

 // rect is now (-50, -200, 350, 500)
 ASSERT(rect == CRect(-50, -200, 350, 500));  
```
  
##  <a name="intersectrect"></a>CRect::IntersectRect  
 使`CRect`相等的两个现有的矩形的交集。  
  
```  
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();  
```  
  
### <a name="parameters"></a>参数  
 `lpRect1`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`对象，其中包含源矩形。  
  
 `lpRect2`  
 指向`RECT`结构或`CRect`对象，其中包含源矩形。  
  
### <a name="return-value"></a>返回值  
 如果交集不为空，则为非零如果交集为空，则为 0。  
  
### <a name="remarks"></a>备注  
 交集是两个现有的矩形中包含的最大矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rectOne(125, 0, 150, 200);
 CRect rectTwo(0, 75, 350,  95);
 CRect rectInter;

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
  
##  <a name="isrectempty"></a>CRect::IsRectEmpty  
 确定是否`CRect`为空。  
  
```  
BOOL IsRectEmpty() const throw();
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CRect`空; 0 如果`CRect`不为空。  
  
### <a name="remarks"></a>备注  
 矩形为空如果的宽度和/或高度值为 0 或负数。 不同于`IsRectNull`，它确定是否所有的矩形的坐标为零。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rectNone(0, 0, 0, 0);
 CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());   
```

  
##  <a name="isrectnull"></a>CRect::IsRectNull  
 确定是否底部上、 左和右值`CRect`所有等于 0。  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CRect`的顶部，左、 下、 和正确的值是所有等于 0; 否则为 0。  
  
### <a name="remarks"></a>备注  
 不同于`IsRectEmpty`，它确定矩形是否为空。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rectNone(0, 0, 0, 0);
 CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
 // note that null means _all_ zeros

 CRect rectNotNull(0, 0, 35, 50);
 ASSERT(!rectNotNull.IsRectNull());  
```
  
##  <a name="movetox"></a>CRect::MoveToX  
 调用此函数可将该矩形移到指定的绝对 x 坐标*x*。  
  
```  
void MoveToX(int x) throw();  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 矩形的左上角绝对 x 坐标。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToX(10);

```cpp  
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));   
```
  
##  <a name="movetoxy"></a>CRect::MoveToXY  
 调用此函数可移动到绝对 x 坐标和 y 坐标指定的矩形。  
  
```  
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 矩形的左上角绝对 x 坐标。  
  
 *y*  
 矩形的左上角绝对 y 坐标。  
  
 `point`  
 A**点**结构，它指定的矩形的绝对的左上角。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToXY(10, 10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));   
```

  
##  <a name="movetoy"></a>CRect::MoveToY  
 调用此函数可将该矩形移到指定的绝对 y 坐标*y*。  
  
```  
void MoveToY(int y) throw();  
```  
  
### <a name="parameters"></a>参数  
 *y*  
 矩形的左上角绝对 y 坐标。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToY(10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));   
```

  
##  <a name="normalizerect"></a>Crect:: Normalizerect  
 规范化`CRect`，以便为正数，高度和宽度。  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>备注  
 矩形被规范化为第四个象限定位，Windows 通常使用的坐标。 `NormalizeRect`比较的顶部和底部的值，并且如果顶部大于底部交换它们。 同样，如果左侧大于右侧交换左侧和右侧值。 此函数与不同的映射模式处理时十分有用，并反转矩形。  
  
> [!NOTE]
>  以下`CRect`成员函数需要规范化的矩形才能正常工作：[高度](#height)，[宽度](#width)，[大小](#size)， [IsRectEmpty](#isrectempty)， [PtInRect](#ptinrect)， [EqualRect](#equalrect)， [UnionRect](#unionrect)， [IntersectRect](#intersectrect)， [SubtractRect](#subtractrect)，[运算符 = =](#operator_eq_eq)，[运算符 ！ =](#operator_neq)，[运算符 &#124;](#operator_or)，[运算符 &#124; =](#operator_or_eq)，[运算符 （& a)](#operator_amp)，和[运算符 & =](#operator_amp_eq)。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(110, 100, 250, 310);
 CRect rect2(250, 310, 110, 100);

```cpp  
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
   rect2.NormalizeRect();
 ASSERT(rect1 == rect2);  
```
  
##  <a name="offsetrect"></a>CRect::OffsetRect  
 将移动`CRect`由指定的偏移量。  
  
```  
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要向左移动或向右的量。 它必须是负值以向左移动。  
  
 *y*  
 指定要向上或向下移动的量。 它必须是负值以向上移动。  
  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或[CPoint](cpoint-class.md)对象，它指定要移动两个维度。  
  
 `size`  
 包含[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](csize-class.md)对象，它指定要移动两个维度。  
  
### <a name="remarks"></a>备注  
 将移动`CRect` *x*沿 x 轴单位和*y*沿 y 轴的单元。 *X*和*y*参数是带符号的值，因此`CRect`可以向左移动或向右和向上或向下。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(0, 0, 35, 35);
 rect.OffsetRect(230, 230);

```cpp  
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));   
```

  
##  <a name="operator_lpcrect"></a>CRect::operator LPCRECT 将`CRect`到[LPCRECT](../../mfc/reference/data-types-mfc.md)。  

  
```  
operator LPCRECT() const throw();
```  
  
### <a name="remarks"></a>备注  
 当你使用此函数时，你不需要的地址 (**&**) 运算符。 传递时，此运算符将可自动用于`CRect`对要求的函数对象**LPCRECT**。  
  

##  <a name="operator_lprect"></a>CRect::operator LPRECT  
 将转换`CRect`到[LPRECT](../../mfc/reference/data-types-mfc.md)。  

  
```
operator LPRECT() throw();
```  
  
### <a name="remarks"></a>备注  
 当你使用此函数时，你不需要的地址 (**&**) 运算符。 传递时，此运算符将可自动用于`CRect`对要求的函数对象`LPRECT`。  
  
### <a name="example"></a>示例  
 请参阅示例[CRect::operator LPCRECT](#operator_lpcrect)。  
  
##  <a name="operator_eq"></a>CRect::operator =  
 将分配*srcRect*到`CRect`。  
  
```  
void operator=(const RECT& srcRect) throw();
```  
  
### <a name="parameters"></a>参数  
 *srcRect*  
 是指源矩形。 可以是[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(0, 0, 127, 168);
 CRect rect2;

```cpp  
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));   
```

  
##  <a name="operator_eq_eq"></a>CRect::operator = =  
 确定是否`rect`等同于`CRect`通过比较其左上角和右下角的坐标。  
  
```  
BOOL operator==(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 是指源矩形。 可以是[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>返回值  
 非零，如果相等;否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(35, 150, 10, 25);
 CRect rect2(35, 150, 10, 25);
 CRect rect3(98, 999,  6,  3);

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

  
##  <a name="operator_neq"></a>CRect::operator ！ =  
 确定是否`rect`是否不等于`CRect`通过比较其左上角和右下角的坐标。  
  
```  
BOOL operator!=(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 是指源矩形。 可以是[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>返回值  
 如果不等于; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(35, 150, 10, 25);
 CRect rect2(35, 150, 10, 25);
 CRect rect3(98, 999,  6,  3);

```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1 != rect3);
 // works just fine against RECTs, as well

 RECT test;
 test.left = 35;
 test.top = 150;
 test.right = 10;
 test.bottom = 25;

 ASSERT(rect3 != test);  
```
  
##  <a name="operator_add_eq"></a>CRect::operator + =  
 前两个重载移动`CRect`由指定的偏移量。  
  
```  
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 A[点](../../mfc/reference/point-structure1.md)结构或[CPoint](cpoint-class.md)对象，它指定要移动矩形的单位数。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](csize-class.md)对象，它指定要移动矩形的单位数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`对象，其中包含要放大量的每一侧的单位数`CRect`。  
  
### <a name="remarks"></a>备注  
 参数的*x*和*y* (或`cx`和`cy`) 值添加到`CRect`。  
  
 第三个重载放大`CRect`中参数的每个成员的单位指定的数。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(100, 235, 200, 335);
 CPoint pt(35, 65);
 CRect rect2(135, 300, 235, 400);

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);   
```
  
##  <a name="operator_-_eq"></a>CRect::operator =  
 前两个重载移动`CRect`由指定的偏移量。  
  
```  
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 A[点](../../mfc/reference/point-structure1.md)结构或[CPoint](cpoint-class.md)对象，它指定要移动矩形的单位数。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](csize-class.md)对象，它指定要移动矩形的单位数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`对象，其中包含要 deflate 的每一侧的单位数`CRect`。  
  
### <a name="remarks"></a>备注  
 参数的*x*和*y* (或`cx`和`cy`) 值相减从`CRect`。  
  
 第三个重载压缩`CRect`中参数的每个成员的单位指定的数。 请注意，此重载方法的功能类似[DeflateRect](#deflaterect)。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(100, 235, 200, 335);
 CPoint pt(35, 65);
 rect1 -= pt;

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);   
```
  
##  <a name="operator_amp_eq"></a>CRect::operator&amp;=  
 集`CRect`相等的交集`CRect`和`rect`。  
  
```  
void operator&=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 包含[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="remarks"></a>备注  
 交集是两个矩形中包含的最大矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 请参阅示例[CRect::IntersectRect](#intersectrect)。  
  
##  <a name="operator_or_eq"></a>CRect::operator &#124; =  
 集`CRect`等于的联合`CRect`和`rect`。  
  
```  
void operator|=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 包含`CRect`或[RECT](../../mfc/reference/rect-structure1.md)。  
  
### <a name="remarks"></a>备注  
 联合是包含两个源矩形的最小矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(100,   0, 200, 300);
 CRect rect2( 0, 100, 300, 200);
 rect1 |= rect2;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);   
```

  
##  <a name="operator_add"></a>CRect::operator +  
 前两个重载返回`CRect`对象，它等于`CRect`移置开指定的偏移量。  
  
```  
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 A[点](../../mfc/reference/point-structure1.md)结构或[CPoint](cpoint-class.md)对象，它指定要移动的返回值的单位数。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](csize-class.md)对象，它指定要移动的返回值的单位数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`对象，其中包含要放大量的返回值的每一侧的单位数。  
  
### <a name="return-value"></a>返回值  
 `CRect`导致移动或 inflating`CRect`的参数中指定的单位数。  
  
### <a name="remarks"></a>备注  
 参数的*x*和*y* (或`cx`和`cy`) 参数添加到`CRect`的位置。  
  
 第三个重载返回一个新`CRect`，它等于`CRect`放大中参数的每个成员的单位指定的数。  
  
### <a name="example"></a>示例  
```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);   
```

  
##  <a name="operator_-"></a>CRect::operator-  
 前两个重载返回`CRect`对象，它等于`CRect`移置开指定的偏移量。  
  
```  
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 A[点](../../mfc/reference/point-structure1.md)结构或`CPoint`对象，它指定要移动的返回值的单位数。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或`CSize`对象，它指定要移动的返回值的单位数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`对象，其中包含要 deflate 的返回值的每一侧的单位数。  
  
### <a name="return-value"></a>返回值  
 `CRect`导致移动或以放气`CRect`的参数中指定的单位数。  
  
### <a name="remarks"></a>备注  
 参数的*x*和*y* (或`cx`和`cy`) 从减去参数`CRect`的位置。  
  
 第三个重载返回一个新`CRect`，它等于`CRect`伸缩单位指定参数的每个成员中的数。 请注意，此重载方法的功能类似[DeflateRect](#deflaterect)，而不[SubtractRect](#subtractrect)。  
  
### <a name="example"></a>示例  
```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);   
```

  
##  <a name="operator_amp"></a>CRect::operator&amp;  
 返回`CRect`即的交集`CRect`和*rect2*。  
  
```  
CRect operator&(const RECT& rect2) const throw();
```  
  
### <a name="parameters"></a>参数  
 *rect2*  
 包含[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>返回值  
 A`CRect`即的交集`CRect`和*rect2*。  
  
### <a name="remarks"></a>备注  
 交集是两个矩形中包含的最大矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);   
```

  
##  <a name="operator_or"></a>CRect::operator &#124;  
 返回`CRect`即的联合`CRect`和*rect2*。  
  
```   
CRect operator|(const RECT& 
rect2) const throw(); 
```  
  
### <a name="parameters"></a>参数  
 *rect2*  
 包含[RECT](../../mfc/reference/rect-structure1.md)或`CRect`。  
  
### <a name="return-value"></a>返回值  
 A`CRect`即的联合`CRect`和*rect2*。  
  
### <a name="remarks"></a>备注  
 联合是包含两个矩形的最小矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect1(100,   0, 200, 300);
 CRect rect2( 0, 100, 300, 200);
 CRect rect3;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```

  
##  <a name="ptinrect"></a>CRect::PtInRect  
 确定指定的点是否位于内`CRect`。  
  
```   
BOOL PtInRect(POINT point) const throw(); 
```  
  
### <a name="parameters"></a>参数  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或[CPoint](cpoint-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果在该点则不为`CRect`; 否则为 0。  
  
### <a name="remarks"></a>备注  
 点位于`CRect`如果它位于上的向左或前一侧或在所有四个边都内。 在右侧或底部端点位于外部`CRect`。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化该矩形。  
  
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
  
##  <a name="setrect"></a>CRect::SetRect  
 设置的尺寸`CRect`为指定的坐标。  
  
```   
void SetRect(int x1, int y1, int x2, int y2) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定的左上角的 x 坐标。  
  
 `y1`  
 指定的左上角的 y 坐标。  
  
 `x2`  
 指定的右下角的 x 坐标。  
  
 `y2`  
 指定的右下角的 y 坐标。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect;
 rect.SetRect(256, 256, 512, 512);

```cpp  
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));   
```

  
##  <a name="setrectempty"></a>CRect::SetRectEmpty  
 使`CRect`通过设置为零的所有坐标 null 矩形。  
  
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
  
##  <a name="size"></a>CRect::SIZE 
 `cx`和`cy`的返回值的成员包含高度和宽度`CRect`。  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>返回值  
 A [CSize](csize-class.md)对象，其中包含的大小`CRect`。  
  
### <a name="remarks"></a>备注  
 高度或宽度可以是负值。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
```cpp  
 CRect rect(10, 10, 50, 50);
 CSize sz = rect.Size();
 ASSERT(sz.cx == 40 && sz.cy == 40);  
```

##  <a name="subtractrect"></a>CRect::SubtractRect  
 使的尺寸**CRect**等于减去`lpRectSrc2`从`lpRectSrc1`。  
  
```  
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpRectSrc1`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或`CRect`从中矩形是要减去的对象。  
  
 `lpRectSrc2`  
 指向`RECT`结构或`CRect`指向对象是被减数矩形`lpRectSrc1`参数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 减法是包含所有中的点的最小矩形`lpRectScr1`位于不在的交集`lpRectScr1`和*lpRectScr2*。  
  
 由指定的矩形`lpRectSrc1`将保持不变，如果指定的矩形`lpRectSrc2`不完全重叠由指定的矩形*lpRectSrc1*中至少一个的 x 或 y 的方向。  
  
 例如，如果`lpRectSrc1`已 10,10 (100100） 和`lpRectSrc2`已 （50,50、 150,150） 指向矩形`lpRectSrc1`函数返回时将保持不变。 如果`lpRectSrc1`已 10,10 (100100） 和`lpRectSrc2`已 50,10 (150,150），但是，在该矩形的指向`lpRectSrc1`将包含坐标为 （10,10，50100） 函数返回时。  
  
 `SubtractRect`不能与相同[运算符-](#operator_-)也不[运算符-=](#operator_-_eq)。 这些运算符任一曾经调用`SubtractRect`。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
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
  
##  <a name="topleft"></a>CRect::TopLeft  
 作为对引用返回坐标[CPoint](cpoint-class.md)中包含的对象`CRect`。  
  
```  
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 矩形左上角的坐标。  
  
### <a name="remarks"></a>备注  
 此函数可用于获取或设置矩形左上角。 通过在赋值运算符的左侧使用此函数中设置角。  
  
### <a name="example"></a>示例  
 请参阅示例[CRect::CenterPoint](#centerpoint)。  
  
##  <a name="unionrect"></a>CRect::UnionRect  
 使的尺寸`CRect`等于两个源矩形的联合。  
  
```  
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpRect1`  
 指向[RECT](../../mfc/reference/rect-structure1.md)或`CRect`，其中包含源矩形。  
  
 `lpRect2`  
 指向`RECT`或`CRect`，其中包含源矩形。  
  
### <a name="return-value"></a>返回值  
 如果联合不为空; 则为非 0如果联合为空，则为 0。  
  
### <a name="remarks"></a>备注  
 联合是包含两个源矩形的最小矩形。  
  
 Windows 将忽略为空矩形; 的尺寸也就是说，没有高度或具有没有宽度的矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```
 
##  <a name="width"></a>CRect::Width  
 计算的宽度`CRect`通过减去右值的左的值。  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>返回值  
 宽度`CRect`。  
  
### <a name="remarks"></a>备注  
 宽度可以是负值。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 你可以调用[NormalizeRect](#normalizerect)调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  

```cpp  
   CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);   
```
## <a name="see-also"></a>请参阅  
 [CPoint 类](cpoint-class.md)   
 [CSize 类](csize-class.md)   
 [RECT](../../mfc/reference/rect-structure1.md)


