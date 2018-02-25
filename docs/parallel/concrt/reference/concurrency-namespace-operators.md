---
title: "concurrency 命名空间运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad453a764a87d0d7e54b914b935fd46f56cd4cac
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空间运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|  
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|  
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)|  
  
##  <a name="operator_lor"></a>  operator&#124;&#124; Operator  
 创建将在作为自变量提供的任一任务成功完成时成功完成的任务。  
  
```  
template<typename ReturnType>  
task<ReturnType> operator||(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void> operator||(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>参数  
 `ReturnType`  
 已返回任务的类型。  
  
 `lhs`  
 要合并到结果任务的第一个任务。  
  
 `rhs`  
 要合并到结果任务的第二个任务。  
  
### <a name="return-value"></a>返回值  
 在输入任务中任何一个成功完成时成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。  
  
### <a name="remarks"></a>备注  
 如果两个任务均被取消或引发异常，则返回的任务将在已取消状态下完成，并且当您对此任务调用 `get()` 或 `wait()` 时将引发一种异常（在遇到异常的情况下）。  
  
##  <a name="operator_amp_amp"></a>  operator&amp;&amp; Operator  
 创建一个任务，在作为自变量提供的两个任务成功完成后，此任务将成功完成。  
  
```  
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void>  operator&&(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>参数  
 `ReturnType`  
 已返回任务的类型。  
  
 `lhs`  
 要合并到结果任务的第一个任务。  
  
 `rhs`  
 要合并到结果任务的第二个任务。  
  
### <a name="return-value"></a>返回值  
 将在两个输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。  
  
### <a name="remarks"></a>备注  
 如果其中一个任务被取消或引发异常，则返回的任务将提前完成（处于已取消状态），并且，如果您对该任务调用 `get()` 或 `wait()`，则在遇到异常的情况下将会引发异常。  
  
##  <a name="operator_eq_eq"></a>  operator== Operator  
 测试运算符左侧的 `concurrent_vector` 对象是否等于右侧的 `concurrent_vector` 对象。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `A1`  
 第一个分配器类型`concurrent_vector`对象。  
  
 `A2`  
 第二个的分配器类型`concurrent_vector`对象。  
  
 `_A`  
 一个 `concurrent_vector` 类型的对象。  
  
 `_B`  
 一个 `concurrent_vector` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果运算符左侧的并发向量等于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 两个并发向量相等，如果它们都有相同的元素数并且它们各自的元素具有相同的值。 否则，它们不相等。  
  
 此方法不是并发安全相对于其他方法，可以修改并发向量任一`_A`或`_B`。  
  
##  <a name="operator_neq"></a>  运算符 ！ = 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否不等于右侧的 `concurrent_vector` 对象。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `A1`  
 第一个分配器类型`concurrent_vector`对象。  
  
 `A2`  
 第二个的分配器类型`concurrent_vector`对象。  
  
 `_A`  
 一个 `concurrent_vector` 类型的对象。  
  
 `_B`  
 一个 `concurrent_vector` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果并发向量是否不相等;`false`如果并发向量相等。  
  
### <a name="remarks"></a>备注  
 两个并发向量相等，如果它们都有相同的元素数并且它们各自的元素具有相同的值。 否则，它们不相等。  
  
 此方法不是并发安全相对于其他方法，可以修改并发向量任一`_A`或`_B`。  
  
##  <a name="operator_lt"></a>  运算符&lt;运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否小于右侧的 `concurrent_vector` 对象。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `A1`  
 第一个分配器类型`concurrent_vector`对象。  
  
 `A2`  
 第二个的分配器类型`concurrent_vector`对象。  
  
 `_A`  
 一个 `concurrent_vector` 类型的对象。  
  
 `_B`  
 一个 `concurrent_vector` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果运算符左侧的并发向量小于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改并发向量任一`_A`或`_B`。  
  
##  <a name="operator_lt_eq"></a>  运算符&lt;= 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否小于或等于右侧的 `concurrent_vector` 对象。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `A1`  
 第一个分配器类型`concurrent_vector`对象。  
  
 `A2`  
 第二个的分配器类型`concurrent_vector`对象。  
  
 `_A`  
 一个 `concurrent_vector` 类型的对象。  
  
 `_B`  
 一个 `concurrent_vector` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果运算符左侧的并发向量小于或等于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改并发向量任一`_A`或`_B`。  
  
##  <a name="operator_gt"></a>  运算符&gt;运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否大于右侧的 `concurrent_vector` 对象。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `A1`  
 第一个分配器类型`concurrent_vector`对象。  
  
 `A2`  
 第二个的分配器类型`concurrent_vector`对象。  
  
 `_A`  
 一个 `concurrent_vector` 类型的对象。  
  
 `_B`  
 一个 `concurrent_vector` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的并发向量大于运算符右侧的并发向量，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改并发向量任一`_A`或`_B`。  
  
##  <a name="operator_gt_eq"></a>  运算符&gt;= 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否大于或等于右侧的 `concurrent_vector` 对象。  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `A1`  
 第一个分配器类型`concurrent_vector`对象。  
  
 `A2`  
 第二个的分配器类型`concurrent_vector`对象。  
  
 `_A`  
 一个 `concurrent_vector` 类型的对象。  
  
 `_B`  
 一个 `concurrent_vector` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果运算符左侧的并发向量大于或等于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改并发向量任一`_A`或`_B`。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
