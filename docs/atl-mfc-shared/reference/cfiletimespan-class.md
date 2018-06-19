---
title: CFileTimeSpan 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: facf4abc01ed55ec7c6d84755530a776c68e166d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362733"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 类
此类提供用于管理相对日期和时间值与文件相关联的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CFileTimeSpan
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|调用此方法以检索从的时间跨度`CFileTimeSpan`对象。|  
|[CFileTimeSpan::SetTimeSpan](#settimespan)|调用此方法以设置的时间跨度内`CFileTimeSpan`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CFileTimeSpan::operator-](#operator_-)|对执行减法`CFileTimeSpan`对象。|  
|[CFileTimeSpan::operator ！ =](#operator_neq)|比较两个 `CFileTimeSpan` 对象是否相等。|  
|[CFileTimeSpan::operator +](#operator_add)|在执行添加`CFileTimeSpan`对象。|  
|[CFileTimeSpan::operator + =](#operator_add_eq)|在执行添加`CFileTimeSpan`对象，并将结果赋给当前对象。|  
|[CFileTimeSpan::operator &lt;](#operator_lt)|比较两个`CFileTimeSpan`对象以确定较小。|  
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|比较两个`CFileTimeSpan`对象以确定是否相等或较小。|  
|[CFileTimeSpan::operator =](#operator_eq)|赋值运算符中。|  
|[CFileTimeSpan::operator =](#operator_-_eq)|对执行减法`CFileTimeSpan`对象，并将结果赋给当前对象。|  
|[CFileTimeSpan::operator = =](#operator_eq_eq)|比较两个 `CFileTimeSpan` 对象是否相等。|  
|[CFileTimeSpan::operator &gt;](#operator_gt)|比较两个`CFileTimeSpan`对象以确定较大。|  
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|比较两个`CFileTimeSpan`对象以确定是否相等或较大。|  
  
## <a name="remarks"></a>备注  
 此类提供了用于管理相对的时间段的方法时执行操作时有关通常遇到的时间的文件已创建、 上次访问或上次修改时间。 此类的方法通常用在结合[CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)对象。  
  
## <a name="example"></a>示例  
 请参阅示例[CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)。  
  
## <a name="requirements"></a>要求  
 **标头：** atltime.h  
  
##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan  
 构造函数。  
  
```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 一个现有的 `CFileTimeSpan` 对象。  
  
 `nSpan`  
 以毫秒为单位的时间段。  
  
### <a name="remarks"></a>备注  
 `CFileTimeSpan`可以使用现有创建对象`CFileTimeSpan`对象，或表示为一个 64 位值。 默认构造函数将设置为 0 的时间跨度。  
  
##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan  
 调用此方法以检索从的时间跨度`CFileTimeSpan`对象。  
  
```
LONGLONG GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回以毫秒为单位的时间跨度。  
  
##  <a name="operator_-"></a>  CFileTimeSpan::operator-  
 对执行减法**CFileTimeSpan**对象。  
  
```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 一个 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回`CFileTimeSpan`表示结果的两个时间范围之间的差异的对象。  
  
##  <a name="operator_neq"></a>  CFileTimeSpan::operator ！ =  
 比较两个 `CFileTimeSpan` 对象是否相等。  
  
```
bool operator!=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 要比较的 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**要比较的项是否不等于`CFileTimeSpan`对象; 否则为**false**。  
  
##  <a name="operator_add"></a>  CFileTimeSpan::operator +  
 在执行添加`CFileTimeSpan`对象。  
  
```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 一个 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回`CFileTimeSpan`对象包含两个时间之和跨越。  
  
##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator + =  
 在执行添加`CFileTimeSpan`对象，并将结果赋给当前对象。  
  
```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 一个 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CFileTimeSpan`对象包含两个时间之和跨越。  
  
##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;  
 比较两个`CFileTimeSpan`对象以确定较小。  
  
```
bool operator<(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 要比较的 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否小于 （也就是说，表示较短的时间段） 第二个，否则为**false**。  
  
##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=  
 比较两个`CFileTimeSpan`对象以确定是否相等或较小。  
  
```
bool operator<=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 要比较的 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果第一个对象小于 （也就是说，表示较短的时间段） 或等于第二个，否则**false**。  
  
##  <a name="operator_eq"></a>  CFileTimeSpan::operator =  
 赋值运算符中。  
  
```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 一个 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CFileTimeSpan`对象。  
  
##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator =  
 对执行减法`CFileTimeSpan`对象，并将结果赋给当前对象。  
  
```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 一个 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CFileTimeSpan`对象。  
  
##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator = =  
 比较两个 `CFileTimeSpan` 对象是否相等。  
  
```
bool operator==(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 要比较的 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果对象相等，否则**false**。  
  
##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;  
 比较两个`CFileTimeSpan`对象以确定较大。  
  
```
bool operator>(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 要比较的 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否大于 （也就是说，表示更长的时间） 第二个，否则为**false**。  
  
##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=  
 比较两个`CFileTimeSpan`对象以确定是否相等或较大。  
  
```
bool operator>=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 要比较的 `CFileTimeSpan` 对象。  
  
### <a name="return-value"></a>返回值  
 返回**true**的第一个对象是否大于 （也就是说，表示更长的时间） 或等于第二个，否则**false**。  
  
##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan  
 调用此方法以设置的时间跨度内`CFileTimeSpan`对象。  
  
```
void SetTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>参数  
 `nSpan`  
 以毫秒为单位的时间跨度新值。  
  
## <a name="see-also"></a>请参阅  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)


