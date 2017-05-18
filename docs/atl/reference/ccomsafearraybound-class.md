---
title: "CComSafeArrayBound 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1cc2adef85c902b7ad12b152b35a7ef68e6abacb
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 类
此类是包装器[SAFEARRAYBOUND](http://msdn.microsoft.com/en-us/303a9bdb-71d6-4f14-8747-84cf84936c6d)结构。  
  
## <a name="syntax"></a>语法  
  
```
class CComSafeArrayBound : public SAFEARRAYBOUND
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComSafeArrayBound](#ccomsafearraybound)|构造函数。|  
|[GetCount](#getcount)|调用此方法以返回元素的数目。|  
|[GetLowerBound](#getlowerbound)|调用此方法以返回下界。|  
|[GetUpperBound](#getupperbound)|调用此方法以返回上限。|  
|[SetCount](#setcount)|调用此方法以设置的元素数。|  
|[SetLowerBound](#setlowerbound)|调用此方法以设置下界。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|集`CComSafeArrayBound`为新值。|  
  
## <a name="remarks"></a>备注  
 此类是包装器**SAFEARRAYBOUND**所用结构[CComSafeArray](../../atl/reference/ccomsafearray-class.md)。 它提供方法用于查询和设置的单个维度的上限和下限边界`CComSafeArray`对象和它所包含的元素数。 多维`CComSafeArray`对象使用的数组`CComSafeArrayBound`对象，为每个维度的一个对象。 因此，使用方法，如[GetCount](#getcount)，请注意，此方法不会对多维数组中返回元素总数。  
  
 **标头：** atlsafe.h  
  
## <a name="requirements"></a>要求  
 **标头：** atlsafe.h  
  
##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound  
 构造函数。  
  
```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `ulCount`  
 数组中的元素数。  
  
 `lLowerBound`  
 从数组已编号的下限。  
  
### <a name="remarks"></a>备注  
 如果阵列为从 Visual c + + 程序进行访问，建议下界被定义为 0。 它可能倾向于使用不同的下限值，如果数组为要与其他语言，如 Visual Basic 使用。  
  
##  <a name="getcount"></a>CComSafeArrayBound::GetCount  
 调用此方法以返回元素的数目。  
  
```
ULONG GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回元素的数。  
  
### <a name="remarks"></a>备注  
 如果关联`CComSafeArray`对象表示多维数组，则此方法将仅在最右边的维度中返回元素总数。 使用[CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount)若要获取的元素总数。  
  
##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound  
 调用此方法以返回下界。  
  
```
LONG GetLowerBound() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回下限为`CComSafeArrayBound`对象。  
  
##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound  
 调用此方法以返回上限。  
  
```
LONG GetUpperBound() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的上限`CComSafeArrayBound`对象。  
  
### <a name="remarks"></a>备注  
 上限取决于元素和下限值的数量。 例如，如果元素的数目为 10 的下限是 0，上限将自动设置为 9。  
  
##  <a name="operator_eq"></a>CComSafeArrayBound::operator =  
 集`CComSafeArrayBound`为新值。  
  
```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>参数  
 `bound`  
 一个 `CComSafeArrayBound` 对象。  
  
 `ulCount`  
 元素数量。  
  
### <a name="return-value"></a>返回值  
 返回一个指向`CComSafeArrayBound`对象。  
  
### <a name="remarks"></a>备注  
 `CComSafeArrayBound`对象可以使用现有分配`CComSafeArrayBound`，或是通过提供顺序案例下限默认设置为 0 的元素数。  
  
##  <a name="setcount"></a>CComSafeArrayBound::SetCount  
 调用此方法以设置的元素数。  
  
```
ULONG SetCount(ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>参数  
 `ulCount`  
 元素数量。  
  
### <a name="return-value"></a>返回值  
 返回中的元素数`CComSafeArrayBound`对象。  
  
##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound  
 调用此方法以设置下界。  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>参数  
 `lLowerBound`  
 下限。  
  
### <a name="return-value"></a>返回值  
 返回新下限为`CComSafeArrayBound`对象。  
  
### <a name="remarks"></a>备注  
 如果阵列为从 Visual c + + 程序进行访问，建议下界被定义为 0。 它可能倾向于使用不同的下限值，如果数组为要与其他语言，如 Visual Basic 使用。  
  
 上限取决于元素和下限值的数量。 例如，如果元素的数目为 10 的下限是 0，上限将自动设置为 9。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

