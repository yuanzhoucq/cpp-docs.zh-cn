---
title: ATL 运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcbe04fb057ffc8077f422cd784b5d31691df1e3
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/10/2018
---
# <a name="atl-operators"></a>ATL 运算符
本部分包含有关 ATL 全局运算符的参考主题。  
  
|运算符|描述|  
|--------------|-----------------|  
|[operator ==](#operator_eq_eq)|比较两个`CSid`对象或`SID`是否相等的结构。|  
|[operator !=](#operator_neq)|比较两个`CSid`对象或`SID`是否不相等的结构。|  
|[operator <](#operator_lt)|如果测试`CSid`对象或`SID`运算符左侧的结构是小于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
|[operator >](#operator_gt)|如果测试`CSid`对象或`SID`运算符左侧的结构是大于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
|[operator <=](#operator_lt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
|[operator >=](#operator_gt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|  
  
## <a name="requirements"></a>要求  
 **标头：** atlsecurity.h。  
  
##  <a name="operator_eq_eq"></a>  operator ==  
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
  
##  <a name="operator_gt"></a>  operator >  
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
  
##  <a name="operator_gt__eq"></a>  operator >=  
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



