---
title: CPen 类
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364070"
---
# <a name="cpen-class"></a>CPen 类

封装一个 Windows 图形设备接口 (GDI) 笔。

## <a name="syntax"></a>语法

```
class CPen : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPen：CPen](#cpen)|构造 `CPen` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPen：：创建笔](#createpen)|创建具有指定样式、宽度和画笔属性的逻辑修饰笔或几何笔，并将其附加到`CPen`对象。|
|[CPen：创建间接](#createpenindirect)|创建具有[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)结构中给定的样式、宽度和颜色的笔，并将其附加到`CPen`对象。|
|[CPen：从手柄](#fromhandle)|在给定 Windows `CPen` HPEN 时返回指向对象的指针。|
|[CPen：获取ExtLogPen](#getextlogpen)|获取[EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)基础结构。|
|[CPen：获取LogPen](#getlogpen)|获取[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)基础结构。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CPen：：操作员 HPEN](#operator_hpen)|返回附加到`CPen`对象的 Windows 句柄。|

## <a name="remarks"></a>备注

有关 使用`CPen`的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen：CPen

构造 `CPen` 对象。

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>参数

*nPenStyle*<br/>
指定笔样式。 构造函数的第一版本中的此参数可以是以下值之一：

- PS_SOLID 创建实心笔。

- PS_DASH创建虚线笔。 仅当笔宽度为 1 或更少时（以设备单位为单位）才有效。

- PS_DOT创建虚笔。 仅当笔宽度为 1 或更少时（以设备单位为单位）才有效。

- PS_DASHDOT创建具有交替破折号和点的笔。 仅当笔宽度为 1 或更少时（以设备单位为单位）才有效。

- PS_DASHDOTDOT创建具有交替破折号和双点的笔。 仅当笔宽度为 1 或更少时（以设备单位为单位）才有效。

- PS_NULL创建空笔。

- PS_INSIDEFRAME 创建一个笔，在 Windows GDI 输出函数`Ellipse`（例如， 、 `Rectangle`、`RoundRect`和`Pie``Chord`成员函数） 生成的封闭形状框架内绘制一条线。 当此样式与不指定边界矩形（例如`LineTo`成员函数）的 Windows GDI 输出函数一起使用时，笔的绘图区域不受框架的限制。

构造函数的第`CPen`二个版本指定类型、样式、结束上限和联接属性的组合。 每个类别中的值应使用位或运算符 （&#124;）进行组合。 笔类型可以是以下值之一：

- PS_GEOMETRIC创建几何笔。

- PS_COSMETIC创建一个化妆笔。

   构造函数的第`CPen`二个版本为*nPenStyle*添加了以下笔样式 ：

- PS_ALTERNATE 创建一个可设置其他像素的笔。 （此样式仅适用于化妆笔。

- PS_USERSTYLE 创建使用用户提供的样式数组的笔。

   端盖可以是以下值之一：

- PS_ENDCAP_ROUND端盖是圆形的。

- PS_ENDCAP_SQUARE端盖是方形的。

- PS_ENDCAP_FLAT端盖是平的。

   联接可以是以下值之一：

- PS_JOIN_BEVEL联接是被否决的。

- PS_JOIN_MITER联接在[SetMiter Limit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit)函数设置的当前限制内时，将小入。 如果联接超过此限制，则将其所仿。

- PS_JOIN_ROUND联接是圆的。

*n 宽度*<br/>
指定笔的宽度。

- 对于构造函数的第一个版本，如果此值为 0，则无论映射模式如何，设备单位的宽度始终为 1 像素。

- 对于构造函数的第二个版本，如果*nPenStyle* PS_GEOMETRIC，则宽度以逻辑单位表示。 如果*nPenStyle* PS_COSMETIC，则必须将宽度设置为 1。

*crColor*<br/>
包含笔的 RGB 颜色。

*pLogBrush*<br/>
指向结构`LOGBRUSH`。 如果*nPenStyle*是PS_COSMETIC，`LOGBRUSH`则结构的*lbColor*成员指定笔的颜色，并且必须将结构的`LOGBRUSH` *lbStyle*成员设置为BS_SOLID。 如果*nPenStyle* PS_GEOMETRIC，则必须使用所有成员指定笔的画笔属性。

*n样式计数*<br/>
指定*lpStyle*数组的长度（以双字单位为单位）。 如果*nPenStyle*不是PS_USERSTYLE，则此值必须为零。

*lpStyle*<br/>
指向双字值数组。 第一个值指定用户定义样式中第一个虚线的长度，第二个值指定第一个空格的长度，等等。 如果未PS_USERSTYLE *nPenStyle，* 则此指针必须为 NULL。

### <a name="remarks"></a>备注

如果使用没有参数的构造函数，`CPen`则必须使用`CreatePen`初始化生成的对象 ，`CreatePenIndirect`或`CreateStockObject`成员函数。

如果使用采用参数的构造函数，则无需进一步初始化。 如果遇到错误，带参数的构造函数可以引发异常，而没有参数的构造函数将始终成功。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen：：创建笔

创建具有指定样式、宽度和画笔属性的逻辑修饰笔或几何笔，并将其附加到`CPen`对象。

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>参数

*nPenStyle*<br/>
指定笔的样式。 有关可能值的列表，请参阅[CPen](#cpen)构造函数中的*nPenStyle*参数。

*n 宽度*<br/>
指定笔的宽度。

- 对于 的第一个版本`CreatePen`，如果此值为 0，则无论映射模式如何，设备单位的宽度始终为 1 像素。

- 对于 的第二个版本`CreatePen`，如果*nPenStyle* PS_GEOMETRIC，则宽度以逻辑单位表示。 如果*nPenStyle* PS_COSMETIC，则必须将宽度设置为 1。

*crColor*<br/>
包含笔的 RGB 颜色。

*pLogBrush*<br/>
指向[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。 如果*nPenStyle* PS_COSMETIC，`lbColor``LOGBRUSH`则结构成员指定笔的颜色，并且必须将结构的`LOGBRUSH` *lbStyle*成员设置为BS_SOLID。 如果 nPenStyle PS_GEOMETRIC，则必须使用所有成员指定笔的画笔属性。

*n样式计数*<br/>
指定*lpStyle*数组的长度（以双字单位为单位）。 如果*nPenStyle*不是PS_USERSTYLE，则此值必须为零。

*lpStyle*<br/>
指向双字值数组。 第一个值指定用户定义样式中第一个虚线的长度，第二个值指定第一个空格的长度，等等。 如果未PS_USERSTYLE *nPenStyle，* 则此指针必须为 NULL。

### <a name="return-value"></a>返回值

如果成功，则为非零;如果方法失败，则为零。

### <a name="remarks"></a>备注

第一个版本的初始`CreatePen`化具有指定样式、宽度和颜色的笔。 随后，可以为任何设备上下文选择笔作为当前笔。

宽度大于 1 像素的笔应始终具有PS_NULL、PS_SOLID或PS_INSIDEFRAME样式。

如果笔具有PS_INSIDEFRAME样式和与逻辑颜色表中的颜色不匹配的颜色，则笔将绘制为抖红色。 PS_SOLID笔样式不能用于创建具有抖红色的笔。 如果笔宽度小于或等于 1，则样式PS_INSIDEFRAME与PS_SOLID相同。

第二个版本的初始`CreatePen`化逻辑修饰笔或几何笔具有指定的样式、宽度和画笔属性。 化妆笔的宽度始终为 1;几何笔的宽度始终以世界单位指定。 应用程序创建逻辑笔后，可以通过调用[CDC：：SelectObject](../../mfc/reference/cdc-class.md#selectobject)函数选择该笔到设备上下文中。 将笔选择到设备上下文中后，它可用于绘制线条和曲线。

- 如果*nPenStyle* PS_COSMETIC和PS_USERSTYLE，*则 lpStyle*数组中的条目以样式单位指定破折号和空格的长度。 样式单元由笔用于绘制线条的设备定义。

- 如果*nPenStyle*是PS_GEOMETRIC和PS_USERSTYLE，则*lpStyle*数组中的条目以逻辑单位指定破折号和空格的长度。

- 如果*nPenStyle* PS_ALTERNATE，则忽略样式单元，并设置所有其他像素。

当应用程序不再需要给定的笔时，它应该调用[CGdiObject：:DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数或销毁`CPen`对象，以便资源不再使用。 在设备上下文中选择笔时，应用程序不应删除笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen：创建间接

初始化具有*lpLogPen*指向的结构中给出的样式、宽度和颜色的笔。

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>参数

*lpLogPen*<br/>
指向包含笔信息的 Windows [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)结构。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

宽度大于 1 像素的笔应始终具有PS_NULL、PS_SOLID或PS_INSIDEFRAME样式。

如果笔具有PS_INSIDEFRAME样式和与逻辑颜色表中的颜色不匹配的颜色，则笔将绘制为抖红色。 如果笔宽度小于或等于 1，则PS_INSIDEFRAME样式与PS_SOLID相同。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>CPen：从手柄

返回指向给定 Windows `CPen` GDI 笔对象的句柄的对象的指针。

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>参数

*hPen*<br/>
`HPEN`句柄到 Windows GDI 笔。

### <a name="return-value"></a>返回值

指向`CPen`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

如果 `CPen` 对象未附加到该句柄，则会创建并附加一个临时 `CPen` 对象。 此临时`CPen`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时图形对象。 换句话说，临时对象仅在处理一个窗口消息期间有效。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>CPen：获取ExtLogPen

获取`EXTLOGPEN`基础结构。

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>参数

*pLogPen*<br/>
指向包含笔信息的[EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

结构`EXTLOGPEN`定义笔的样式、宽度和画笔属性。 例如，调用`GetExtLogPen`以匹配笔的特定样式。

有关笔属性的信息，请参阅 Windows SDK 中的以下主题：

- [获取对象](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [洛彭](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>示例

以下代码示例演示了调用`GetExtLogPen`检索笔的属性，然后创建具有相同颜色的新修饰笔。

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen：获取LogPen

获取`LOGPEN`基础结构。

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>参数

*pLogPen*<br/>
指向[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)结构以包含有关笔的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

结构`LOGPEN`定义笔的样式、颜色和图案。

例如，调用`GetLogPen`以匹配笔的特定样式。

有关笔属性的信息，请参阅 Windows SDK 中的以下主题：

- [获取对象](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [洛彭](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>示例

以下代码示例演示了调用`GetLogPen`以检索笔字符，然后创建具有相同颜色的新实心笔。

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen：：操作员 HPEN

获取`CPen`对象的附加 Windows GDI 句柄。

```
operator HPEN() const;
```

### <a name="return-value"></a>返回值

如果成功，则对对象表示的 Windows GDI`CPen`对象的句柄;如果成功，则对对象表示的 Windows GDI 对象的句柄。否则 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HPEN 对象。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>另请参阅

[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[画笔类](../../mfc/reference/cbrush-class.md)
