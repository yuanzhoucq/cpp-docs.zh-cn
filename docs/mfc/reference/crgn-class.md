---
title: CRgn 类
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: e84526eec8f4fd4b1935fa39bc7f4ed3c4d5dd71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754486"
---
# <a name="crgn-class"></a>CRgn 类

封装一个 Windows 图形设备接口 (GDI) 区域。

## <a name="syntax"></a>语法

```
class CRgn : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CRgn：CRgn](#crgn)|构造 `CRgn` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRgn：：联合Rgn](#combinergn)|设置`CRgn`对象，使其等效于两个指定`CRgn`对象的联合。|
|[CRgn：：复制Rgn](#copyrgn)|设置`CRgn`对象，使其是指定`CRgn`对象的副本。|
|[CRgn：：创造椭圆形](#createellipticrgn)|使用椭圆区域`CRgn`初始化对象。|
|[CRgn：：创造椭圆形间接](#createellipticrgnindirect)|初始化具有由`CRgn` [RECT](/windows/win32/api/windef/ns-windef-rect)结构定义的椭圆区域的对象。|
|[CRgn：：从数据创建](#createfromdata)|从给定区域创建区域和转换数据。|
|[CRgn：：从路径创建](#createfrompath)|从所选到给定设备上下文的路径创建区域。|
|[CRgn：：创造波隆龙](#createpolygonrgn)|使用多边形区域`CRgn`初始化对象。 如有必要，系统通过绘制从最后一个顶点到第一个顶点的线自动关闭面。|
|[CRgn：：创造多聚贡](#createpolypolygonrgn)|初始化`CRgn`对象，其区域由一系列闭合多边形组成。 多边形可能不交，也可能重叠。|
|[CRgn：：创建RectRgn](#createrectrgn)|使用矩形区域初始`CRgn`化对象。|
|[CRgn：：创建rectRgn间接](#createrectrgnindirect)|初始化具有由`CRgn` [RECT](/windows/win32/api/windef/ns-windef-rect)分Truture 定义的矩形区域的对象。|
|[CRgn：：创建圆形雷茨尔格](#createroundrectrgn)|使用圆角的`CRgn`矩形区域初始化对象。|
|[CRgn：：平等Rgn](#equalrgn)|检查两`CRgn`个对象以确定它们是否等效。|
|[CRgn：：从手柄](#fromhandle)|当为 Windows`CRgn`区域指定句柄时，返回指向对象的指针。|
|[CRgn：获取区域数据](#getregiondata)|使用描述给定区域的数据填充指定的缓冲区。|
|[CRgn：：GetRgnBox](#getrgnbox)|检索`CRgn`对象边界矩形的坐标。|
|[CRgn：：偏移Rgn](#offsetrgn)|按指定的`CRgn`偏移量移动对象。|
|[CRgn：:Ptin区域](#ptinregion)|确定指定点是否位于该区域中。|
|[CRgn：：Rectin 区域](#rectinregion)|确定指定矩形的任何部分是否位于区域的边界内。|
|[CRgn：：塞特勒克·雷克根](#setrectrgn)|将`CRgn`对象设置到指定的矩形区域。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CRgn：：操作员 HRGN](#operator_hrgn)|返回`CRgn`对象中包含的 Windows 句柄。|

## <a name="remarks"></a>备注

区域是窗口中的椭圆或多边形区域。 要使用区域，请使用类`CRgn`的成员函数，其中的剪辑函数定义为类`CDC`的成员。

`CRgn`创建、更改和检索有关为其调用它们的区域对象的信息的成员函数。

有关 使用`CRgn`的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn：：联合Rgn

通过合并两个现有区域创建新的 GDI 区域。

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>参数

*pRgn1*<br/>
标识现有区域。

*pRgn2*<br/>
标识现有区域。

*n合并模式*<br/>
指定合并两个源区域时要执行的操作。 它可以是以下任一值：

- RGN_AND 使用两个区域（交集）的重叠区域。

- RGN_COPY 创建区域 1 的副本（由*pRgn1*标识）。

- RGN_DIFF 创建一个区域，由区域 1（由*pRgn1*标识）的区域组成，区域 2 不属于区域 2（由*pRgn2*标识）。

- RGN_OR将两个区域全部合并（联合）。

- RGN_XOR合并两个区域，但删除重叠区域。

### <a name="return-value"></a>返回值

指定生成的区域的类型。 可以为下列值之一：

- 复杂区域 新区域具有重叠边框。

- 错误 未创建新区域。

- NULL 区域 新区域为空。

- SIMPLE区域 新区域没有重叠边框。

### <a name="remarks"></a>备注

区域按*nCombineMode*指定进行组合。

两个指定的区域合并在一起，生成的区域句柄存储在对象中`CRgn`。 因此，`CRgn`对象中存储的任何区域都将替换为组合区域。

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

使用[CopyRgn](#copyrgn)只需将一个区域复制到另一个区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn：：复制Rgn

将*pRgnSrc*定义的区域复制到对象`CRgn`中。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>参数

*普根斯克*<br/>
标识现有区域。

### <a name="return-value"></a>返回值

指定生成的区域的类型。 可以为下列值之一：

- 复杂区域 新区域具有重叠边框。

- 错误 未创建新区域。

- NULL 区域 新区域为空。

- SIMPLE区域 新区域没有重叠边框。

### <a name="remarks"></a>备注

新区域替换以前存储在对象中的`CRgn`区域。 此函数是[组合 Rgn](#combinergn)成员函数的特例。

### <a name="example"></a>示例

  请参阅[CRgn 的示例：：创建椭圆。](#createellipticrgn)

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn：：创造椭圆形

创建椭圆区域。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定椭圆边界矩形左上角的逻辑 x 坐标。

*y1*<br/>
指定椭圆边界矩形左上角的逻辑 y 坐标。

*x2*<br/>
指定椭圆边界矩形右下角的逻辑 x 坐标。

*y2*<br/>
指定椭圆边界矩形右下角的逻辑 y 坐标。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

该区域由*x1、y1* *、x2*和*y1* *y2*指定的边界矩形定义。 该区域存储在对象中`CRgn`。

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

使用使用`CreateEllipticRgn`函数创建的区域完成后，应用程序应从设备上下文中选择该区域，并使用函数`DeleteObject`将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn：：创造椭圆形间接

创建椭圆区域。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向包含椭`RECT`圆边界矩形`CRect`左上角和右下角逻辑坐标的结构或对象。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

区域由*lpRect*指向的结构或对象定义，并存储在对象中`CRgn`。

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

使用使用`CreateEllipticRgnIndirect`函数创建的区域完成后，应用程序应从设备上下文中选择该区域，并使用函数`DeleteObject`将其删除。

### <a name="example"></a>示例

  请参阅[CRgn 的示例：：创建 RectRgn 间接](#createrectrgnindirect)。

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn：：从数据创建

从给定区域创建区域和转换数据。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>参数

*lpXForm*<br/>
指向定义要在区域上执行的转换的[XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata 结构。 如果此指针为 NULL，则使用标识转换。

*nCount*<br/>
指定*pRgnData*指向的字节数。

*pRgnData*<br/>
指向包含区域数据的[RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata)数据结构。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过调用`CRgn::GetRegionData`函数来检索区域的数据。

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn：：从路径创建

从所选到给定设备上下文的路径创建区域。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
标识包含闭合路径的设备上下文。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

*pDC*参数标识的设备上下文必须包含闭合路径。 将`CreateFromPath`路径转换为区域后，Windows 将从设备上下文中丢弃关闭的路径。

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn：：创造波隆龙

创建多边形区域。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>参数

*lpPoints*<br/>
指向`POINT`结构数组或`CPoint`对象数组。 每个结构指定多边形一个顶点的 x 坐标和 y 坐标。 结构`POINT`具有以下形式：

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
指定*lpPoints*指向`CPoint`的数组中`POINT`的结构或对象数。

*nMode*<br/>
指定区域的填充模式。 此参数可以是 ALTERNATE 或 WINDING。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

如有必要，系统通过绘制从最后一个顶点到第一个顶点的线自动关闭面。 生成的区域存储在对象中`CRgn`。

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

当多边形填充模式为 ALTERNATE 时，系统将填充每个扫描行上的奇数和偶数多边形边之间的区域。 也就是说，系统填充第一和第二侧之间的区域，在第三和第四侧之间，等等。

当多边形填充模式为 WINDING 时，系统使用绘制图形的方向来确定是否填充区域。 多边形中的每个线段都以顺时针或逆时针方向绘制。 每当从封闭区域绘制到图形外部的虚线经过顺时针线段时，计数就会递增。 当线通过逆时针线段时，计数将递减。 如果计数在行到达图形外部时计数为非零，则填充该区域。

当应用程序使用使用`CreatePolygonRgn`函数创建的区域完成时，它应从设备上下文中选择该区域，并使用函数`DeleteObject`将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn：：创造多聚贡

创建由一系列闭合多边形组成的区域。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>参数

*lpPoints*<br/>
指向结构数组`POINT`或定义多边形顶点`CPoint`的对象数组。 必须显式关闭每个面，因为系统不会自动关闭它们。 连续指定多边形。 结构`POINT`具有以下形式：

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
指向整数数组。 第一个整数指定*lpPoints*数组中第一个多边形中的顶点数，第二个整数指定第二个多边形中的顶点数，等等。

*nCount*<br/>
指定*lpPolyCounts*数组中的整数总数。

*nPolyFill模式下*<br/>
指定多边形填充模式。 此值可以是 ALTERNATE 或 WINDING。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

生成的区域存储在对象中`CRgn`。

多边形可能不交，也可能重叠。

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

当多边形填充模式为 ALTERNATE 时，系统将填充每个扫描行上的奇数和偶数多边形边之间的区域。 也就是说，系统填充第一和第二侧之间的区域，在第三和第四侧之间，等等。

当多边形填充模式为 WINDING 时，系统使用绘制图形的方向来确定是否填充区域。 多边形中的每个线段都以顺时针或逆时针方向绘制。 每当从封闭区域绘制到图形外部的虚线经过顺时针线段时，计数就会递增。 当线通过逆时针线段时，计数将递减。 如果计数在行到达图形外部时计数为非零，则填充该区域。

当应用程序使用使用`CreatePolyPolygonRgn`函数创建的区域完成时，它应该从设备上下文中选择该区域，并使用[CGDIObject：:DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数来删除它。

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn：：创建RectRgn

创建存储在对象中的`CRgn`矩形区域。

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定区域左上角的逻辑 x 坐标。

*y1*<br/>
指定区域左上角的逻辑 y 坐标。

*x2*<br/>
指定区域右下角的逻辑 x 坐标。

*y2*<br/>
指定区域右下角的逻辑 y 坐标。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

应用程序在完成使用 由 创建的`CreateRectRgn`区域后，应使用[CGDIObject：:DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数删除该区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

有关其他示例，请参阅[CRgn：：合并Rgn](#combinergn)。

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn：：创建rectRgn间接

创建存储在对象中的`CRgn`矩形区域。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向包含区域`RECT`左上`CRect`角和右下角的逻辑坐标的结构或对象。 结构`RECT`具有以下形式：

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

应用程序在完成使用 由 创建的`CreateRectRgnIndirect`区域后，应使用[CGDIObject：:DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数删除该区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn：：创建圆形雷茨尔格

创建一个矩形区域，其圆角存储在对象中`CRgn`。

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定区域左上角的逻辑 x 坐标。

*y1*<br/>
指定区域左上角的逻辑 y 坐标。

*x2*<br/>
指定区域右下角的逻辑 x 坐标。

*y2*<br/>
指定区域右下角的逻辑 y 坐标。

*x3*<br/>
指定用于创建圆角的椭圆的宽度。

*y3*<br/>
指定用于创建圆角的椭圆的高度。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

区域的大小限制为 32，767 个逻辑单元或 64K 内存（以较小者为准）。

当应用程序使用使用`CreateRoundRectRgn`函数创建的区域完成时，它应该从设备上下文中选择该区域，并使用[CGDIObject：:DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数来删除它。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn：CRgn

构造 `CRgn` 对象。

```
CRgn();
```

### <a name="remarks"></a>备注

在`m_hObject`使用一个或多个其他成员`CRgn`函数初始化对象之前，数据成员不包含有效的 Windows GDI 区域。

### <a name="example"></a>示例

  请参阅[CRgn 的示例：：创建RoundrectRgn](#createroundrectrgn)。

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn：：平等Rgn

确定给定区域是否等效于存储在对象中的`CRgn`区域。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>参数

*pRgn*<br/>
标识区域。

### <a name="return-value"></a>返回值

如果两个区域等效，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn：：从手柄

当为 Windows`CRgn`区域指定句柄时，返回指向对象的指针。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>参数

*hRgn*<br/>
指定 Windows 区域的句柄。

### <a name="return-value"></a>返回值

一个指向 `CRgn` 对象的指针。 如果函数未成功，则返回值为 NULL。

### <a name="remarks"></a>备注

如果对象`CRgn`尚未附加到句柄，则创建并附加临时`CRgn`对象。 此临时`CRgn`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时图形对象。 另一种说法是临时对象仅在处理一个窗口消息期间有效。

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn：获取区域数据

使用描述区域的数据填充指定的缓冲区。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>参数

*lpRgn数据*<br/>
指向接收信息的[RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata)数据结构。 如果此参数为 NULL，则返回值包含区域数据所需的字节数。

*nCount*<br/>
指定*lpRgnData*缓冲区的大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，并且*nCount*指定足够的字节数，则返回值始终为*nCount*。 如果函数失败，或者如果*nCount*指定的字节数少于足够数，则返回值为 0（错误）。

### <a name="remarks"></a>备注

此数据包括构成区域的矩形的尺寸。 此功能与函数`CRgn::CreateFromData`结合使用。

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn：：GetRgnBox

检索对象边界矩形的`CRgn`坐标。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象以接收边界矩形的坐标。 结构`RECT`具有以下形式：

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>返回值

指定区域的类型。 可以是以下任一值：

- 复杂区域具有重叠边框。

- NULL 区域为空。

- 错误`CRgn`对象不指定有效的区域。

- SIMPLE 区域没有重叠边框。

### <a name="example"></a>示例

  请参阅[CRgn 的示例：：创建 PolygonRgn](#createpolygonrgn)。

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn：：偏移Rgn

按指定的偏移量移动存储在`CRgn`对象中的区域。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>参数

*x*<br/>
指定向左或向右移动的单位数。

*Y*<br/>
指定要向上或向下移动的单位数。

*点*<br/>
*点的*x 坐标指定向左或向右移动的单位数。 *点的*y 坐标指定要向上或向下移动的单位数。 *点*参数可以是`POINT`结构参数，也可以是`CPoint`对象。

### <a name="return-value"></a>返回值

新区域的类型。 它可以是以下任一值：

- 复杂区域具有重叠边框。

- 错误区域句柄无效。

- NULL 区域为空。

- SIMPLE 区域没有重叠边框。

### <a name="remarks"></a>备注

该函数沿 x 轴移动区域*x*单位，沿 y 轴*移动 y*单位。

区域坐标值必须小于或等于 32，767，大于或等于 -32，768。 必须仔细选择*x*和*y*参数，以防止区域坐标无效。

### <a name="example"></a>示例

  请参阅[CRgn 的示例：：创建椭圆。](#createellipticrgn)

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn：：操作员 HRGN

使用此运算符获取`CRgn`对象的附加 Windows GDI 句柄。

```
operator HRGN() const;
```

### <a name="return-value"></a>返回值

如果成功，则对对象表示的 Windows GDI`CRgn`对象的句柄;如果成功，则对对象表示的 Windows GDI 对象的句柄。否则 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HRGN 对象。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的["图形对象](/windows/win32/gdi/graphic-objects)"一文。

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn：:Ptin区域

检查*x*和*y*给出的点是否位于`CRgn`存储在对象中的区域中。

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>参数

*x*<br/>
指定要测试的点的逻辑 x 坐标。

*Y*<br/>
指定要测试的点的逻辑 y 坐标。

*点*<br/>
*点的*x 坐标和 y 坐标指定要测试 的值的点的 x 和 y 坐标。 *点*参数可以是`POINT`结构参数，也可以是`CPoint`对象。

### <a name="return-value"></a>返回值

如果点位于该区域中，则非零;否则 0。

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn：：Rectin 区域

确定*lpRect*指定的矩形的任何部分是否位于存储在`CRgn`对象中的区域的边界内。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象。 结构`RECT`具有以下形式：

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>返回值

如果指定矩形的任何部分位于区域的边界内，则非零;否则 0。

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn：：塞特勒克·雷克根

创建矩形区域。

```cpp
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定矩形区域左上角的 x 坐标。

*y1*<br/>
指定矩形区域左上角的 y 坐标。

*x2*<br/>
指定矩形区域右下角的 x 坐标。

*y2*<br/>
指定矩形区域右下角的 y 坐标。

*lpRect*<br/>
指定矩形区域。 可以是指向结构的指针，`RECT`也可以是`CRect`对象。

### <a name="remarks"></a>备注

但是，与[CreateRectRgn](#createrectrgn)不同，它不从本地 Windows 应用程序堆中分配任何其他内存。 相反，它使用为存储在`CRgn`对象中的区域分配的空间。 这意味着在调用`SetRectRgn``CRgn`之前，对象必须已使用有效的 Windows 区域初始化。 x1、y1、x2 和*x2* *y2*给出的点指定分配空间的最小大小。 *x1* *y1*

使用此函数而不是`CreateRectRgn`成员函数以避免调用本地内存管理器。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
