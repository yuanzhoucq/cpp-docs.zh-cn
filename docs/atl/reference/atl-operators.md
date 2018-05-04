---
title: ATL 运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75c9ffb8c918cce70ad1e150dd80cb07ebdd7b34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="atl-operators"></a>ATL 运算符
本部分包含有关 ATL 全局运算符的参考主题。  
  
|运算符|描述|  
|--------------|-----------------|  
|[operator ==](#operator_eq_eq)|比较两个`CSid`对象或`SID`是否相等的结构。|  
|[运算符 ！ =](#operator_neq)|比较两个`CSid`对象或`SID`是否不相等的结构。|  
|[运算符 <](#operator_lt)|如果测试`CSid`对象或`SID`运算符左侧的结构是小于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
|[运算符 >](#operator_gt)|如果测试`CSid`对象或`SID`运算符左侧的结构是大于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
|[运算符 < =](#operator_lt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
|[运算符 > =](#operator_gt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
  
## <a name="requirements"></a>要求  
 **标头：** atlsecurity.h。  
  
##  <a name="operator_eq_eq"></a>  运算符 = =  
 比较`CSid`对象或`SID`（安全标识符） 结构是否相等。  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果对象相等， **false**如果它们不相等。  
  
##  <a name="operator_neq"></a>  运算符 ！ =  
 比较`CSid`对象或`SID`（安全标识符） 结构是否不相等。  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**对象是否不相等，如果**false**如果它们是否相等。  
  
##  <a name="operator_lt"></a>  运算符 <  
 如果测试`CSid`对象或`SID`运算符左侧的结构是小于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果的地址`lhs`对象是否的地址小于`rhs`对象， **false**否则为。  
  
### <a name="remarks"></a>备注  
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供 c + + 标准库集合类与兼容性。  
  
##  <a name="operator_gt"></a>  运算符 >  
 如果测试`CSid`对象或`SID`运算符左侧的结构是大于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果的地址`lhs`大于的地址`rhs`， **false**否则为。  
  
### <a name="remarks"></a>备注  
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供 c + + 标准库集合类与兼容性。  
  
##  <a name="operator_lt__eq"></a>  运算符 < =  
 如果测试`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果的地址`lhs`小于或等于的地址`rhs`， **false**否则为。  
  
### <a name="remarks"></a>备注  
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供 c + + 标准库集合类与兼容性。  
  
##  <a name="operator_gt__eq"></a>  运算符 > =  
 如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果的地址`lhs`大于或等于的地址`rhs`， **false**否则为。  
  
### <a name="remarks"></a>备注  
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供 c + + 标准库集合类与兼容性。



