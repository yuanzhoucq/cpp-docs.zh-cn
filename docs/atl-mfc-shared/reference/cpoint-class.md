---
title: CPoint 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36dc82c03f13b4708d705d9fd66eff26870c8346
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365388"
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
|[CPoint::CPoint](#cpoint)|构造一个 `CPoint`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPoint::Offset](#offset)|将值添加到**x**和**y**的成员`CPoint`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CPoint::operator-](#operator_-)|返回的差异`CPoint`和大小或求反运算的一个点或两个点或按负的大小的偏移量之间的大小差异。|  
|[CPoint::operator ！ =](#operator_neq)|检查两个点之间不相等。|  
|[CPoint::operator +](#operator_add)|返回的总和`CPoint`、 大小或点，或`CRect`相对大小的偏移量。|  
|[CPoint::operator + =](#operator_add_eq)|偏移量`CPoint`通过添加大小或点。|  
|[CPoint::operator =](#operator_-_eq)|偏移量`CPoint`通过减去大小或点。|  
|[CPoint::operator = =](#operator_eq_eq)|检查两个点之间相等。|  
  
## <a name="remarks"></a>备注  
 它还包括成员函数以操作`CPoint`和[点](../../mfc/reference/point-structure1.md)结构。  
  
 A`CPoint`对象可以是任何位置使用`POINT`使用结构。 此类与"大小"交互的运算符接受[CSize](../../atl-mfc-shared/reference/csize-class.md)对象或[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，因为这两个是可互换。  
  
> [!NOTE]
>  此类派生自`tagPOINT`结构。 (名称`tagPOINT`是较不常用的名称`POINT`结构。)这意味着的数据成员`POINT`结构，`x`和`y`，可访问的数据成员的`CPoint`。  
  
> [!NOTE]
>  有关详细信息共享实用程序类 (如`CPoint`)，请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `tagPOINT`  
  
 `CPoint`  
  
## <a name="requirements"></a>要求  
 **标头：** atltypes.h  
  
##  <a name="cpoint"></a>  CPoint::CPoint
 构造 `CPoint` 对象。  
  
```  
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```  
  
### <a name="parameters"></a>参数  
 `initX`  
 指定 `x` 的 `CPoint` 成员的值。  
  
 `initY`  
 指定 `y` 的 `CPoint` 成员的值。  
  
 `initPt`  
 [点](../../mfc/reference/point-structure1.md)结构或`CPoint`，它指定用于初始化的值`CPoint`。  
  
 `initSize`  
 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md) ，它指定用于初始化的值`CPoint`。  
  
 `dwPoint`  
 将 `x` 成员设置为 `dwPoint` 的低位字，并将 `y` 成员设置为 `dwPoint` 的高位字。  
  
### <a name="remarks"></a>备注  
 如果未提供参数，则 `x` 和 `y` 成员将设置为 0。  
  
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
  
##  <a name="offset"></a>  CPoint::Offset  
 将值添加到**x**和**y**的成员`CPoint`。  
  
```  
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```  
  
### <a name="parameters"></a>参数  
 *拼音*  
 指定的偏移量**x**的成员`CPoint`。  
  
 *正文*  
 指定的偏移量**y**的成员`CPoint`。  
  
 `point`  
 指定的量 ([点](../../mfc/reference/point-structure1.md)或`CPoint`) 的偏移`CPoint`。  
  
 `size`  
 指定的量 ([大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)或[CSize](../../atl-mfc-shared/reference/csize-class.md)) 的偏移`CPoint`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CPoint::operator = =  
 检查两个点之间相等。  
  
```  
BOOL operator==(POINT point) const throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或`CPoint`对象。  
  
### <a name="return-value"></a>返回值  
 如果点相等，则非零否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]  
  
##  <a name="operator_neq"></a>  CPoint::operator ！ =  
 检查两个点之间不相等。  
  
```  
BOOL operator!=(POINT point) const throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或`CPoint`对象。  
  
### <a name="return-value"></a>返回值  
 如果点是否不相等; 则为非 0否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>  CPoint::operator + =  
 第一个重载将添加到大小`CPoint`。  
  
```  
void operator+=(SIZE size) throw(); 
void operator+=(POINT point) throw();
```  
  
### <a name="parameters"></a>参数  
 `size`  
 包含[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
### <a name="remarks"></a>备注  
 第二个重载添加到一个点`CPoint`。  
  
 在这两种情况下，添加可通过添加**x** (或**cx**) 的右侧操作数的成员**x**的成员`CPoint`和添加**y** (或**cy**) 的右侧操作数的成员**y**的成员`CPoint`。  
  
 例如，添加`CPoint(5, -7)`给一个变量，其中包含`CPoint(30, 40)`更改变量`CPoint(35, 33)`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>  CPoint::operator =  
 第一个重载中减去从大小`CPoint`。  
  
```  
void operator-=(SIZE size) throw(); 
void operator-=(POINT point) throw();
```  
  
### <a name="parameters"></a>参数  
 `size`  
 包含[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
### <a name="remarks"></a>备注  
 第二个重载减去中的点`CPoint`。  
  
 在这两种情况下，减法是通过减去**x** (或**cx**) 从右侧操作数的成员**x**的成员`CPoint`和减去**y** (或**cy**) 从右侧操作数的成员**y**的成员`CPoint`。  
  
 例如，减去`CPoint(5, -7)`从变量包含`CPoint(30, 40)`更改变量`CPoint(25, 47)`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]  
  
##  <a name="operator_add"></a>  CPoint::operator +  
 使用此运算符将偏移量`CPoint`通过`CPoint`或`CSize`对象，或以偏移量`CRect`通过`CPoint`。  
  
```  
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```  
  
### <a name="parameters"></a>参数  
 `size`  
 包含[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
 `point`  
 包含[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
 `lpRect`  
 包含指向的[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 A`CPoint`大小偏移**CPoint**点偏移或**CRect**按点偏移。  
  
### <a name="remarks"></a>备注  
 例如，使用前两个重载之一的偏移点`CPoint(25, -19)`点`CPoint(15, 5)`或大小`CSize(15, 5)`返回的值`CPoint(40, -14)`。  
  
 向点添加一个矩形按偏移后返回的矩形**x**和**y**点中指定的值。 例如，使用的最后一个重载偏移矩形`CRect(125, 219, 325, 419)`点`CPoint(25, -19)`返回`CRect(150, 200, 350, 400)`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]  
  
##  <a name="operator_-"></a>  CPoint::operator-  
 使用前两个重载之一来减去`CPoint`或`CSize`对象`CPoint`。  
  
```  
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```  
  
### <a name="parameters"></a>参数  
 `point`  
 A[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
 `size`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
 `lpRect`  
 指向的指针[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 A `CSize` ，它是两个点之间的差异`CPoint`求反运算的一个大小，偏移`CRect`求反运算的一个点，偏移或`CPoint`，它是一个点的求反。  
  
### <a name="remarks"></a>备注  
 第三个重载偏移量`CRect`求反结果`CPoint`。 最后，使用一元运算符进行求反运算`CPoint`。  
  
 例如，使用第一个重载，要了解两个点之间的时差`CPoint(25, -19)`和`CPoint(15, 5)`返回`CSize(10, -24)`。  
  
 减去`CSize`从`CPoint`会执行与上述相同的计算，但返回`CPoint`对象，而不`CSize`对象。 例如，使用第二个重载，要了解为点之间的时差`CPoint(25, -19)`和大小`CSize(15, 5)`返回`CPoint(10, -24)`。  
  
 减去矩形从点按的假负返回矩形偏移量**x**和**y**点中指定的值。 例如，使用的最后一个重载偏移矩形`CRect(125, 200, 325, 400)`点`CPoint(25, -19)`返回`CRect(100, 219, 300, 419)`。  
  
 使用一元运算符对一个点。 例如，与点一起使用的一元运算符`CPoint(25, -19)`返回`CPoint(-25, 19)`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [POINT 结构](../../mfc/reference/point-structure1.md)   
 [CRect 类](../../atl-mfc-shared/reference/crect-class.md)   
 [CSize 类](../../atl-mfc-shared/reference/csize-class.md)



