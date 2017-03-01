---
title: "concurrency 命名空间运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 7fc7b500d882bb4e023904a147a7736996b5c5de
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空间运算符
||||  
|-|-|-|  
|[运算符 ！ = 运算符](#operator_neq)|[运算符&amp;&amp;运算符](#operator_amp_amp)|[运算符&gt;运算符](#operator_gt)|  
|[运算符&gt;= 运算符](#operator_gt_eq)|[运算符&lt;运算符](#operator_lt)|[运算符&lt;= 运算符](#operator_lt_eq)|  
|[运算符 = = 运算符](#operator_eq_eq)|[operator|| Operator](#operator_lor)|  
  
##  <a name="a-nameoperatorlora--operator124124-operator"></a><a name="operator_lor"></a>运算符 | |运算符  
 创建将在作为自变量提供的任一任务成功完成时成功完成的任务。  
  
```  
template<
    typename _ReturnType  
>  
task<_ReturnType>   operator||(
    const task<_ReturnType>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>   operator||(
    const task<std::vector<_ReturnType>>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>   operator||(
    const task<_ReturnType>& _Lhs,  
    const task<std::vector<_ReturnType>>& _Rhs);

 
inline task<void>   operator||(
    const task<void>& _Lhs,  
    const task<void>& _Rhs);
```  
  
### <a name="parameters"></a>参数  
 `_ReturnType`  
 已返回任务的类型。  
  
 `_Lhs`  
 要合并到结果任务的第一个任务。  
  
 `_Rhs`  
 要合并到结果任务的第二个任务。  
  
### <a name="return-value"></a>返回值  
 在输入任务中任何一个成功完成时成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。  
  
### <a name="remarks"></a>备注  
 如果两个任务均被取消或引发异常，则返回的任务将在已取消状态下完成，并且当您对此任务调用 `get()` 或 `wait()` 时将引发一种异常（在遇到异常的情况下）。  
  
##  <a name="a-nameoperatorampampa--operatorampamp-operator"></a><a name="operator_amp_amp"></a>运算符&amp;&amp;运算符  
 创建一个任务，在作为自变量提供的两个任务成功完成后，此任务将成功完成。  
  
```  
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<_ReturnType>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<std::vector<_ReturnType>>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<_ReturnType>& _Lhs,  
    const task<std::vector<_ReturnType>>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<std::vector<_ReturnType>>& _Lhs,  
    const task<std::vector<_ReturnType>>& _Rhs);

 
inline task<void>    operator&&(
    const task<void>& _Lhs,  
    const task<void>& _Rhs);
```  
  
### <a name="parameters"></a>参数  
 `_ReturnType`  
 已返回任务的类型。  
  
 `_Lhs`  
 要合并到结果任务的第一个任务。  
  
 `_Rhs`  
 要合并到结果任务的第二个任务。  
  
### <a name="return-value"></a>返回值  
 将在两个输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。  
  
### <a name="remarks"></a>备注  
 如果其中一个任务被取消或引发异常，则返回的任务将提前完成（处于已取消状态），并且，如果您对该任务调用 `get()` 或 `wait()`，则在遇到异常的情况下将会引发异常。  
  
##  <a name="a-nameoperatoreqeqa--operator-operator"></a><a name="operator_eq_eq"></a>运算符 = = 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否等于右侧的 `concurrent_vector` 对象。  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
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
 `true`如果运算符左侧的并发向量等于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 两个并发向量相等，如果它们具有相同数量的元素，并且它们各自的元素具有相同的值。 否则，它们不相等。  
  
 此方法不是并发安全相对于其他方法，可以修改的并发向量任一`_A`或`_B`。  
  
##  <a name="a-nameoperatorneqa--operator-operator"></a><a name="operator_neq"></a>运算符 ！ = 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否不等于右侧的 `concurrent_vector` 对象。  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
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
 `true`如果并发向量是否不相等;`false`如果并发向量相等。  
  
### <a name="remarks"></a>备注  
 两个并发向量相等，如果它们具有相同数量的元素，并且它们各自的元素具有相同的值。 否则，它们不相等。  
  
 此方法不是并发安全相对于其他方法，可以修改的并发向量任一`_A`或`_B`。  
  
##  <a name="a-nameoperatorlta--operatorlt-operator"></a><a name="operator_lt"></a>运算符&lt;运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否小于右侧的 `concurrent_vector` 对象。  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
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
 `true`如果运算符左侧的并发向量小于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改的并发向量任一`_A`或`_B`。  
  
##  <a name="a-nameoperatorlteqa--operatorlt-operator"></a><a name="operator_lt_eq"></a>运算符&lt;= 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否小于或等于右侧的 `concurrent_vector` 对象。  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
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
 `true`如果运算符左侧的并发向量小于或等于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改的并发向量任一`_A`或`_B`。  
  
##  <a name="a-nameoperatorgta--operatorgt-operator"></a><a name="operator_gt"></a>运算符&gt;运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否大于右侧的 `concurrent_vector` 对象。  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
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
  
 此方法不是并发安全相对于其他方法，可以修改的并发向量任一`_A`或`_B`。  
  
##  <a name="a-nameoperatorgteqa--operatorgt-operator"></a><a name="operator_gt_eq"></a>运算符&gt;= 运算符  
 测试运算符左侧的 `concurrent_vector` 对象是否大于或等于右侧的 `concurrent_vector` 对象。  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
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
 `true`如果运算符左侧的并发向量大于或等于运算符; 右侧的并发向量否则为`false`。  
  
### <a name="remarks"></a>备注  
 此运算符的行为等同于为等效的运算符`vector`类`std`命名空间。  
  
 此方法不是并发安全相对于其他方法，可以修改的并发向量任一`_A`或`_B`。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

