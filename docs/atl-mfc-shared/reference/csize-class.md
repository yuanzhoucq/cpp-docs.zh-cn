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
ms.openlocfilehash: 87beb468fb8fe61358a03e2cd287903a268a18ba
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740491"
---
# <a name="csize-class"></a>CSize 类

类似于实现相对坐标或位置的 Windows [SIZE](/windows/desktop/api/windef/ns-windef-tagsize) 结构。

## <a name="syntax"></a>语法

```
class CSize : public tagSIZE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSize::CSize](#csize)|构造 `CSize` 对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSize::operator-](#operator_-)|中减去两个大小。|
|[CSize::operator !=](#operator_neq)|检查之间是否不相等`CSize`和大小。|
|[CSize::operator +](#operator_add)|将添加两个大小。|
|[CSize::operator +=](#operator_add_eq)|添加到大小`CSize`。|
|[CSize::operator -=](#operator_-_eq)|从大小中减去`CSize`。|
|[CSize::operator ==](#operator_eq_eq)|检查是否相等`CSize`和大小。|

## <a name="remarks"></a>备注

此类派生自`SIZE`结构。 这意味着可以将传递`CSize`中为调用的参数`SIZE`并且的数据成员`SIZE`结构是可访问的数据成员的`CSize`。

`cx`并`cy`的成员`SIZE`(和`CSize`) 是公共的。 此外，`CSize`实现成员函数以操作`SIZE`结构。

> [!NOTE]
> 有关详细信息共享实用程序类 (如`CSize`)，请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagSIZE`

`CSize`

## <a name="requirements"></a>要求

**标头：** atltypes.h

##  <a name="csize"></a>  CSize::CSize

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
集`cx`成员为`CSize`。

*initCY*<br/>
集`cy`成员为`CSize`。

*initSize*<br/>
[大小](/windows/desktop/api/windef/ns-windef-tagsize)结构或`CSize`对象，用于初始化`CSize`。

*initPt*<br/>
[点](/windows/desktop/api/windef/ns-windef-tagpoint)结构或`CPoint`对象，用于初始化`CSize`。

*dwSize*<br/>
用于初始化 DWORD `CSize`。 低序位字是`cx`成员和高序位字是`cy`成员。

### <a name="remarks"></a>备注

如果不给定了任何自变量，`cx`和`cy`初始化为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator = =

两个大小之间的相等性检查。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>备注

如果大小相等，则非零，则会返回 otherwize 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>  CSize::operator ！ =

检查两个大小相等的。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>备注

返回非零，如果大小不相等，否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CSize::operator + =

将大小添加到此`CSize`。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CSize::operator -=

从该大小中减去`CSize`。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>  CSize::operator +

这些运算符添加此`CSize`值与参数的值。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>备注

请参阅各个运算符的以下说明：

- **operator +(** *size* **)**

  此操作将添加两个`CSize`值。

- **operator +(** *point* **)**

  此操作的偏移量 （移动）[点](/previous-versions/dd162805\(v=vs.85\))(或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) 值由此`CSize`值。 `cx`并`cy`此成员`CSize`值添加到`x`并`y`的数据成员`POINT`值。 它相当于的新版[CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)采用[大小](/windows/desktop/api/windef/ns-windef-tagsize)参数。

- **operator +(** *lpRect* **)**

   此操作的偏移量 （移动） [RECT](/previous-versions/dd162897\(v=vs.85\)) (或[CRect](../../atl-mfc-shared/reference/crect-class.md)) 值由此`CSize`值。 `cx`并`cy`此成员`CSize`值添加到`left`， `top`， `right`，以及`bottom`的数据成员`RECT`值。 它相当于的新版[CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)采用[大小](/windows/desktop/api/windef/ns-windef-tagsize)参数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>  CSize::operator-

这些运算符的前三个减去此`CSize`值与参数的值。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>备注

第四个运算符，一元负，可更改的登录`CSize`值。 请参阅各个运算符的以下说明：

- **operator -(** *size* **)**

  此操作中减去两个`CSize`值。

- **operator -(** *point* **)**

  此操作的偏移量 （移动）[点](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)值，从而此加法逆元`CSize`值。 `cx`并`cy`此`CSize`减去值`x`并`y`的数据成员`POINT`值。 它相当于的新版[CPoint::operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)采用[大小](/windows/desktop/api/windef/ns-windef-tagsize)参数。

- **operator -(** *lpRect* **)**

  此操作的偏移量 （移动） [RECT](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)值，从而此加法逆元`CSize`值。 `cx`并`cy`此成员`CSize`减去值`left`， `top`， `right`，以及`bottom`的数据成员`RECT`值。 它相当于的新版[CRect::operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-)采用[大小](/windows/desktop/api/windef/ns-windef-tagsize)参数。

- **operator -()**

  此操作将返回此加法逆元`CSize`值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 类](../../atl-mfc-shared/reference/cpoint-class.md)
