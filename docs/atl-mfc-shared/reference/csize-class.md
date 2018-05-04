---
title: CSize 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
dev_langs:
- C++
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18c48ccf2d1d7f424ca9b95f9dcbf7a2953a52aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="csize-class"></a>CSize 类
类似于实现相对坐标或位置的 Windows [SIZE](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构。  
  
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
|[CSize::operator-](#operator_-)|减去两个大小。|  
|[CSize::operator ！ =](#operator_neq)|检查之间是否不相等`CSize`和大小。|  
|[CSize::operator +](#operator_add)|将添加两个大小。|  
|[CSize::operator + =](#operator_add_eq)|添加到大小`CSize`。|  
|[CSize::operator =](#operator_-_eq)|减去从大小`CSize`。|  
|[CSize::operator = =](#operator_eq_eq)|检查之间的相等性`CSize`和大小。|  
  
## <a name="remarks"></a>备注  
 此类派生自**大小**结构。 这意味着你可以通过`CSize`调用的参数中**大小**且的数据成员**大小**结构不是可访问的数据成员的`CSize`。  
  
 **Cx**和**cy**的成员**大小**(和`CSize`) 都是公开的。 此外，`CSize`实现成员函数以操作**大小**结构。  
  
> [!NOTE]
>  有关详细信息共享实用程序类 (如`CSize`)，请参阅[共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
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
 *initCX*  
 集**cx**成员`CSize`。  
  
 *initCY*  
 集**cy**成员`CSize`。  
  
 `initSize`  
 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或`CSize`用于初始化对象`CSize`。  
  
 `initPt`  
 [点](../../mfc/reference/point-structure1.md)结构或`CPoint`用于初始化对象`CSize`。  
  
 `dwSize`  
 `DWORD` 用于初始化`CSize`。 低序位字是**cx**成员且高序位字已**cy**成员。  
  
### <a name="remarks"></a>备注  
 如果未提供参数， **cx**和**cy**初始化为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CSize::operator = =  
 两个大小之间的相等性检查。  
  
```   
BOOL operator==(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>备注  
 如果大小相等，则为非 0，则会返回 otherwize 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]  
  
##  <a name="operator_neq"></a>  CSize::operator ！ =  
 检查两个大小之间不相等。  
  
```   
BOOL operator!=(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>备注  
 返回非零，如果大小不相等; 否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>  CSize::operator + =  
 将大小添加到此`CSize`。  
  
```   
void operator+=(SIZE size) throw(); 
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>  CSize::operator =  
 减去从此大小`CSize`。  
  
```   
void operator-=(SIZE size) throw(); 
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]  
  
##  <a name="operator_add"></a>  CSize::operator +  
 这些运算符添加`CSize`值与参数的值。  
  
```   
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw(); 
```  
  
### <a name="remarks"></a>备注  
 请参阅各个运算符的以下说明：  
  
- **运算符 + (** `size` **)** 此操作将添加两个`CSize`值。  
  
- **运算符 + (** `point` **)** 此操作的偏移量 （移动）[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)(或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) 值由此`CSize`值。 **Cx**和**cy** this 的成员`CSize`值添加到**x**和**y**的数据成员**点**值。 它相当于版本的[CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)采用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)参数。  
  
- **运算符 + (** `lpRect` **)** 此操作的偏移量 （移动） [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) (或[CRect](../../atl-mfc-shared/reference/crect-class.md)) 值由此`CSize`值。 **Cx**和**cy** this 的成员`CSize`值添加到**左**，**顶部**，**右**，和**底部**的数据成员`RECT`值。 它相当于版本的[CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)采用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]  
  
##  <a name="operator_-"></a>  CSize::operator-  
 这些运算符的前三个减去这`CSize`值与参数的值。  
  
```   
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw(); 
```  
  
### <a name="remarks"></a>备注  
 第四个运算符，一元负，改变的符号`CSize`值。 请参阅各个运算符的以下说明：  
  
- **运算符-(** `size` **)** 此操作中减去两个`CSize`值。  
  
- **运算符-(** `point` **)** 此操作的偏移量 （移动）[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)值，通过此加法逆元`CSize`值。 **Cx**和**cy**此`CSize`值相减从**x**和**y**的数据成员**点**值。 它相当于版本的[CPoint::operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)采用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)参数。  
  
- **运算符-(** `lpRect` **)** 此操作的偏移量 （移动） [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)或[CRect](../../atl-mfc-shared/reference/crect-class.md)值，通过此加法逆元`CSize`值。 **Cx**和**cy** this 的成员`CSize`值相减从**左**，**顶部**，**右**，和**底部**的数据成员`RECT`值。 它相当于版本的[CRect::operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-)采用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)参数。  
  
- **运算符-（)** 此操作将返回此加法逆元`CSize`值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRect 类](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint 类](../../atl-mfc-shared/reference/cpoint-class.md)

