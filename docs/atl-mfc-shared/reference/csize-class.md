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
ms.openlocfilehash: 6d1b82e3f60428e3a778709dc69de983a7f886bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317677"
---
# <a name="csize-class"></a>CSize 类

类似于实现相对坐标或位置的 Windows [SIZE](/windows/win32/api/windef/ns-windef-size) 结构。

## <a name="syntax"></a>语法

```
class CSize : public tagSIZE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[大小：大小](#csize)|构造 `CSize` 对象。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CSize：运算符 -](#operator_-)|减去两种大小。|
|[CSize：：操作员！*](#operator_neq)|检查大小之间的`CSize`不等式。|
|[CSize：运算符 |](#operator_add)|添加两种大小。|
|[大小：：操作员 |](#operator_add_eq)|向 添加大小`CSize`到 。|
|[大小：：运算符 -*](#operator_-_eq)|从`CSize`中减去大小。|
|[大小：：运算符 |](#operator_eq_eq)|检查和大小之间的`CSize`相等性。|

## <a name="remarks"></a>备注

此类派生自结构`SIZE`。 这意味着您可以传递 调用`CSize`的`SIZE`参数，并且`SIZE`结构的数据成员是 可`CSize`访问的数据成员。

和`CSize`（ 的成员 ） 是公开的。 `cx` `cy` `SIZE` 此外，`CSize`实现成员函数来操作结构`SIZE`。

> [!NOTE]
> 有关共享实用程序类的详细信息（如`CSize`），请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagSIZE`

`CSize`

## <a name="requirements"></a>要求

**标题：** atltype.h

## <a name="csizecsize"></a><a name="csize"></a>大小：大小

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
`cx`设置 的成员`CSize`。

*因特西*<br/>
`cy`设置 的成员`CSize`。

*initSize*<br/>
[用于](/windows/win32/api/windef/ns-windef-size)初始化`CSize``CSize`的 SIZE 结构或对象。

*initPt*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)用于初始化`CPoint``CSize`的 POINT 结构或对象。

*dwSize*<br/>
DWORD 用于初始化`CSize`。 低阶单词是`cx`成员，高阶单词是`cy`成员。

### <a name="remarks"></a>备注

如果未给出参数，`cx`并且`cy`初始化为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>大小：：运算符 |

检查两种大小之间的相等性。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>备注

如果大小相等，则返回非零，其他为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize：：操作员！*

检查两种大小之间的不等式。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>备注

如果大小不相等，则返回非零，否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>大小：：操作员 |

为此添加大小`CSize`。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>大小：：运算符 -*

从中`CSize`减去大小。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>CSize：运算符 |

这些运算符将此值`CSize`添加到参数的值中。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>备注

请参阅以下各个运算符的说明：

- **运算符 +（** *大小* **）**

  此操作将添加两`CSize`个值。

- **运算符 +（***点***）**

  此操作按此值`CSize`偏移（移动[）POINT（](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)） 值。 此值`cx``CSize`的`cy`和 成员将添加到 值`x``y`和 数据成员`POINT`中。 它类似于[CPoint：：运算符 *](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)的版本，它采用[SIZE](/windows/win32/api/windef/ns-windef-size)参数。

- **运算符 +（** *lpRect* **）**

   此操作按此值`CSize`偏移（移动[）RECT（](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)） 值。 此值`cx``CSize`的`cy`和 成员将添加到`RECT`值`left``top`的`right`、`bottom`和 数据成员中。 它类似于[CRect：：运算符 *](../../atl-mfc-shared/reference/crect-class.md#operator_add)的版本，它采用[SIZE](/windows/win32/api/windef/ns-windef-size)参数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize：运算符 -

这些运算符的前三个将此值`CSize`减去参数的值。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>备注

第四个运算符，一元减号，更改`CSize`值的符号。 请参阅以下各个运算符的说明：

- **运算符 -（** *尺寸* **）**

  此操作减去两`CSize`个值。

- **运算符 -（***点***）**

  此操作按此值`CSize`的累加反反偏移（移动[）POINT](/previous-versions/dd162805\(v=vs.85\))或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)值。 此值`cx`的`cy``CSize`和 将从`x``y``POINT`值 和 数据成员中减去。 它类似于[CPoint：：运算符](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)的版本 - 它采用[SIZE](/windows/win32/api/windef/ns-windef-size)参数。

- 运算符 *-（lpRect）* **)** **operator -(**

  此操作通过此值`CSize`的累加反反偏移（移动[）RECT](/previous-versions/dd162897\(v=vs.85\))或[CRect](../../atl-mfc-shared/reference/crect-class.md)值。 此值`cx``CSize`的`cy`和 成员将从`bottom``RECT`值的`left`、`top`和`right`数据成员中减去。 它类似于[CRect：：：运算符](../../atl-mfc-shared/reference/crect-class.md#operator_-)的版本 - 它采用[SIZE](/windows/win32/api/windef/ns-windef-size)参数。

- **运算符 -（）**

  此操作返回此值`CSize`的累加反数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint 类](../../atl-mfc-shared/reference/cpoint-class.md)
