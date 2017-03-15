---
title: "ATL 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 87aadf7aacc31ded165a8e1380823cb20e614fb1
ms.lasthandoff: 02/24/2017

---
# <a name="atl-operators"></a>ATL 运算符
本部分包含有关 ATL 全局运算符的参考主题。  
  
|运算符|说明|  
|--------------|-----------------|  
|[运算符 = =](#operator_eq_eq)|比较两个`CSid`对象或`SID`结构是否相等。|  
|[运算符 ！ =](#operator_neq)|比较两个`CSid`对象或`SID`结构是否不相等。|  
|[运算符](#operator_lt)|测试如果`CSid`对象或`SID`运算符左侧的结构是不会早于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。|  
|[运算符&1;>](#operator_gt)|测试如果`CSid`对象或`SID`运算符左侧的结构是大于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。|  
|[运算符<>](#operator_lt__eq)|测试如果`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。|  
|[运算符&1;> =](#operator_gt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。|  
  
 这些运算符所有文件 atlsecurity.h 中定义。  
  
##  <a name="a-nameoperatoreqeqa--operator-"></a><a name="operator_eq_eq"></a>运算符 = =  
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
 返回**true**对象是否相等，如果**false**如果它们不相等。  
  
##  <a name="a-nameoperatorneqa--operator-"></a><a name="operator_neq"></a>运算符 ！ =  
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
  
##  <a name="a-nameoperatorlta--operator-"></a><a name="operator_lt"></a>运算符  
 测试如果`CSid`对象或`SID`运算符左侧的结构是不会早于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果的地址`lhs`对象小于的地址`rhs`对象， **false**否则为。  
  
### <a name="remarks"></a>备注  
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。  
  
##  <a name="a-nameoperatorgta--operator-"></a><a name="operator_gt"></a>运算符&1;>  
 测试如果`CSid`对象或`SID`运算符左侧的结构是大于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。  
  
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
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。  
  
##  <a name="a-nameoperatorlteqa--operator-"></a><a name="operator_lt__eq"></a>运算符<=></=>  
 测试如果`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>参数  
 `lhs`  
 第一个`CSid`对象或`SID`结构进行比较。  
  
 `rhs`  
 第二个`CSid`对象或`SID`结构进行比较。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果的地址`lhs`是否小于或等于的地址`rhs`， **false**否则为。  
  
### <a name="remarks"></a>备注  
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。  
  
##  <a name="a-nameoperatorgteqa--operator-"></a><a name="operator_gt__eq"></a>运算符&1;> =  
 如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`右侧 （适用于 c + + 标准库兼容性） 的结构。  
  
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
 此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。




