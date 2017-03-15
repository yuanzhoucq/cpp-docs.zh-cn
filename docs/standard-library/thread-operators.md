---
title: "&lt;thread&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 7e849e8585b372b5b423a6c960aa926ac7d5cfec
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;&lt;](#operator_lt__lt_)|[operator&lt;=](#operator_lt__eq)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>operator&gt;=  
 确定一个 `thread::id` 对象是否大于或等于另一个。  
  
```cpp  
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread::id` 对象。  
  
 `Right`  
 正确的 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 `!(Left < Right)`  
  
### <a name="remarks"></a>备注  
 此函数不引发任何异常。  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>operator&gt;  
 确定一个 `thread::id` 对象是否大于另一个。  
  
```cpp  
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread::id` 对象。  
  
 `Right`  
 正确的 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 `Right < Left`  
  
### <a name="remarks"></a>备注  
 此函数不引发任何异常。  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>operator&lt;=  
 确定一个 `thread::id` 对象是否小于或等于另一个。  
  
```cpp  
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread::id` 对象。  
  
 `Right`  
 正确的 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 `!(Right < Left)`  
  
### <a name="remarks"></a>备注  
 此函数不引发任何异常。  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>operator&lt;  
 确定一个 `thread::id` 对象是否小于另一个。  
  
```cpp  
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread::id` 对象。  
  
 `Right`  
 正确的 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 如果在总排序中，`Left` 超过 `Right`，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 该运算符定义所有 `thread::id` 对象的总排序。 这些对象可以用作关联容器中的键。  
  
 此函数不引发任何异常。  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>operator!=  
 比较两个 `thread::id` 对象是否相等。  
  
```cpp  
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread::id` 对象。  
  
 `Right`  
 正确的 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 `!(Left == Right)`  
  
### <a name="remarks"></a>备注  
 此函数不引发任何异常。  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>operator==  
 比较两个 `thread::id` 对象是否相等。  
  
```cpp  
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread::id` 对象。  
  
 `Right`  
 正确的 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象表示同一个执行线程或者这两个对象都不表示执行线程，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此函数不引发任何异常。  
  
##  <a name="a-nameoperatorltlta--operatorltlt"></a><a name="operator_lt__lt_"></a>operator&lt;&lt;  
 将 `thread::id` 对象的文本表示形式插入流。  
  
```cpp  
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```  
  
### <a name="parameters"></a>参数  
 `Ostr`  
 一个 [basic_ostream](../standard-library/basic-ostream-class.md) 对象。  
  
 `Id`  
 一个 `thread::id` 对象。  
  
### <a name="return-value"></a>返回值  
 `Ostr`。  
  
### <a name="remarks"></a>备注  
 此函数会将 `Id` 插入 `Ostr`。  
  
 如果两个`thread::id` 对象相等，这些对象的文本表示形式相同。  
  
## <a name="see-also"></a>另请参阅  
 [\<thread>](../standard-library/thread.md)




