---
title: "并发命名空间运算符 (AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
dev_langs:
- C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: 676f3e836082dc3286a45f8d59db83c969964058
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-operators-amp"></a>并发命名空间运算符 (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|  
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>operator==   
 确定指定的参数是否相等。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 一个元组进行比较。  
  
 `_Rhs`  
 一个元组进行比较。  
  
### <a name="return-value"></a>返回值  
 `true`如果元组相等，则否则为`false`。  
  
##  <a name="operator_neq"></a>operator!=   
 确定指定的参数是否不相等。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 一个元组进行比较。  
  
 `_Rhs`  
 一个元组进行比较。  
  
### <a name="return-value"></a>返回值  
 `true`如果元组是否不相等;否则为`false`。  
  
##  <a name="operator_add"></a>  operator+   

 计算指定的参数的 component-wise 和。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 要添加的参数之一。  
  
 `_Rhs`  
 要添加的参数之一。  
  
### <a name="return-value"></a>返回值  
 在指定的参数 component-wise 之和。  
  
##  <a name="operator-"></a>operator-   

 计算指定的参数之间的 component-wise 差异。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 要从进行减法运算的参数。  
  
 `_Rhs`  
 要减去的参数。  
  
### <a name="return-value"></a>返回值  
 在指定的参数之间的 component-wise 差异。  
  
##  <a name="operator_star"></a>  operator*   

 计算指定的参数的 component-wise 积。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 要相乘的元组之一。  
  
 `_Rhs`  
 要相乘的元组之一。  
  
### <a name="return-value"></a>返回值  
 在指定的参数 component-wise 产品。  
  

##  <a name="operator_div"></a>  operator/   
 计算指定的参数的 component-wise 商。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 要作为被除数元组。  
  
 `_Rhs`  
 要作为除数元组。  
  
### <a name="return-value"></a>返回值  
 在指定的参数 component-wise 商。  
  
##  <a name="operator_mod"></a>operator%   

 计算的第二个指定的参数的第一个指定参数的模数。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 元组参数的秩。  
  
 `_Lhs`  
 从该元组计算取模。  
  
 `_Rhs`  
 取模由元组，到。  
  
### <a name="return-value"></a>返回值  
 第一个指定的参数取模第二个指定的参数的结果。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace-cpp-amp.md)

