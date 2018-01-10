---
title: "CComSafeArrayBound 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs: C++
helpviewer_keywords: CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4de823b4cdb2d7926b2a9d640b2e8f7352e389fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[GetLowerBound](#getlowerbound)|调用此方法以返回下限。|  
|[GetUpperBound](#getupperbound)|调用此方法以返回上限。|  
|[SetCount](#setcount)|调用此方法以设置的元素数。|  
|[SetLowerBound](#setlowerbound)|调用此方法以设置下限。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|集`CComSafeArrayBound`为新值。|  
  
## <a name="remarks"></a>备注  
 此类是包装器**SAFEARRAYBOUND**使用结构[CComSafeArray](../../atl/reference/ccomsafearray-class.md)。 它提供用于查询和设置的单个维度的上限和下限边界方法`CComSafeArray`对象和它所包含的元素数。 多维`CComSafeArray`对象使用的数组`CComSafeArrayBound`对象，每个维度的一个对象。 因此，如使用方法时[GetCount](#getcount)，请注意，此方法不将多维数组中返回的元素总数。  
  
 **标头：** atlsafe.h  
  
## <a name="requirements"></a>惠?  
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
 从中编号数组的下限。  
  
### <a name="remarks"></a>备注  
 如果数组为从 Visual c + + 程序中访问，建议下限定义为 0。 它可能更可取的方法使用不同的下限值，如果数组为要与 Visual Basic 等其他语言使用。  
  
##  <a name="getcount"></a>CComSafeArrayBound::GetCount  
 调用此方法以返回元素的数目。  
  
```
ULONG GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回元素的数。  
  
### <a name="remarks"></a>备注  
 如果关联`CComSafeArray`对象表示多维数组，此方法将仅在最右边的维度中返回的元素总数。 使用[CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount)若要获取的元素总数。  
  
##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound  
 调用此方法以返回下限。  
  
```
LONG GetLowerBound() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的下限`CComSafeArrayBound`对象。  
  
##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound  
 调用此方法以返回上限。  
  
```
LONG GetUpperBound() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的上限`CComSafeArrayBound`对象。  
  
### <a name="remarks"></a>备注  
 上限取决于元素和下限值的数目。 例如，如果下限为 0 且元素的数目为 10，将自动为 9 设置上限。  
  
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
 `CComSafeArrayBound`可以使用现有分配对象`CComSafeArrayBound`，或提供的元素，在其中用例下限默认设置为 0 的数目。  
  
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
 调用此方法以设置下限。  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>参数  
 `lLowerBound`  
 下限。  
  
### <a name="return-value"></a>返回值  
 返回新的界限低于`CComSafeArrayBound`对象。  
  
### <a name="remarks"></a>备注  
 如果数组为从 Visual c + + 程序中访问，建议下限定义为 0。 它可能更可取的方法使用不同的下限值，如果数组为要与 Visual Basic 等其他语言使用。  
  
 上限取决于元素和下限值的数目。 例如，如果下限为 0 且元素的数目为 10，将自动为 9 设置上限。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
