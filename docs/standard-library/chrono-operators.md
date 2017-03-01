---
title: "&lt;chrono&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
caps.latest.revision: 8
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c2ea4241ef1db4989caf8cdc6a16044d9c9381f6
ms.lasthandoff: 02/24/2017

---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; 运算符
||||  
|-|-|-|  
|[operator modulo](#operator_modulo)|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|  
|[operator&gt;=](#operator_gt__eq)|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|  
|[operator*](#operator_star)|[operator+](#operator_add)|[operator-](#operator-)|  
|[operator/](#operator_)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperator-a--operator-"></a><a name="operator-"></a>  operator-  
 用于对 [duration](../standard-library/duration-class.md) 和 [time_point](../standard-library/time-point-class.md) 对象进行减法或求反运算的运算符。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type 
   operator-(
       const duration<Rep1, Period1>& Left, 
       cconst duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Rep2, class Period2>  
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type  
   operator-(
       const time_point<Clock, Duration1>& Time, 
       const duration<Rep2, Period2>& Dur);

 
template <class Clock, class Duration1, class Duration2>  
constexpr typename common_type<Duration1, Duration2>::type 
   operator-(
       const time_point<Clock, Duration1>& Left, 
       const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
 `Time`  
 一个 `time_point` 对象。  
  
 `Dur`  
 一个 `duration` 对象。  
  
### <a name="return-value"></a>返回值  
 第一个函数返回一个 `duration` 对象，其间隔长度是两个参数的时间间隔之差。  
  
 第二个函数返回一个 `time_point` 对象，该对象表示的时间点替代为对由 `Dur` 表示的时间间隔的求反结果（从由 `Time` 指定的时间点开始）。  
  
 第三个函数返回一个 `duration` 对象，该对象表示 `Left` 和 `Right` 之间的时间间隔。  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象的不等运算符。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);

 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
### <a name="return-value"></a>返回值  
 每个函数均返回 `!(Left == Right)`。  
  
##  <a name="a-nameoperatorstara--operator"></a><a name="operator_star"></a>  operator*  
 [duration](../standard-library/chrono-operators.md#operator_star) 对象的乘法运算符。  
  
```  
template <class Rep1, class Period1, class Rep2>  
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1> 
   operator*(
      const duration<Rep1, Period1>& Dur, 
      const Rep2& Mult);

 
template <class Rep1, class Rep2, class Period2>  
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2> 
   operator*(
       const Rep1& Mult,
       const duration<Rep2, 
       Period2>& Dur);
```  
  
### <a name="parameters"></a>参数  
 `Dur`  
 一个 `duration` 对象。  
  
 `Mult`  
 一个整数值。  
  
### <a name="return-value"></a>返回值  
 每个函数返回一个 `duration` 对象，其间隔长度是 `Dur` 的长度乘以 `Mult`。  
  
 除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>` *“保持为 true”*，否则第一个函数不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。  
  
 除非 `is_convertible<Rep1, common_type<Rep1, Rep2>>` *“保持为 true”*，否则第二个函数不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。  
  
##  <a name="a-nameoperatora--operator"></a><a name="operator_"></a>  operator/  
 [duration](../standard-library/chrono-operators.md#operator_star) 对象的除法运算符。  
  
```  
template <class Rep1, class Period1, class Rep2>  
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1> 
   operator/(
     const duration<Rep1, Period1>& Dur,  
     const Rep2& Div);

 
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<Rep1, Rep2>::type 
   operator/(
     const duration<Rep1, Period1>& Left,  
     const duration<Rep2, Period2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Dur`  
 一个 `duration` 对象。  
  
 `Div`  
 一个整数值。  
  
 `Left`  
 左 `duration` 对象。  
  
 `Right`  
 正确的 `duration` 对象。  
  
### <a name="return-value"></a>返回值  
 第一个运算符返回持续时间对象，该对象的时间间隔长度是 `Dur` 除以值 `Div` 的长度。  
  
 第二个运算符返回 `Left` 和 `Right` 的时间间隔长度的比率。  
  
 除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>` *“保持为 true”*，并且 `Rep2` 不是 `duration` 的实例化，否则第一个运算符不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。  
  
##  <a name="a-nameoperatoradda--operator"></a><a name="operator_add"></a>  operator+  
 添加 [duration](../standard-library/duration-class.md) 和 [time_point](../standard-library/time-point-class.md) 对象。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type 
   operator+(
      const duration<Rep1, Period1>& Left,  
      const duration<Rep2, Period2>& Right);

 
template <class Clock, class Duration1, class Rep2, class Period2>  
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,  
      const duration<Rep2, Period2>& Dur);

 
template <class Rep1, class Period1, class Clock, class Duration2>  
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,  
      const time_point<Clock, Duration2>& Time);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
 `Time`  
 一个 `time_point` 对象。  
  
 `Dur`  
 一个 `duration` 对象。  
  
### <a name="return-value"></a>返回值  
 第一个函数返回 `duration` 对象，该对象具有的时间间隔等同于 `Left` 和 `Right` 之和的时间间隔。  
  
 第二个和第三个函数将返回 `time_point` 对象，该对象表示从时间点 `Time` 由 `Dur` 时间间隔取代的时间点。  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否小于另一个 `duration` 或 `time_point` 对象。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);

 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
### <a name="return-value"></a>返回值  
 如果 `Left` 的间隔长度小于 `Right` 的间隔长度，则第一个函数返回 `true`。 否则，该函数返回 `false`。  
  
 如果 `Left` 先于 `Right`，则第二个函数返回 `true`。 否则，该函数返回 `false`。  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否小于或等于另一个 `duration` 或 `time_point` 对象。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
### <a name="return-value"></a>返回值  
 每个函数均返回 `!(Right < Left)`。  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 确定两个 `duration` 对象是否表示相同长度的时间间隔，或两个 `time_point` 对象是否表示相同的时间点。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
### <a name="return-value"></a>返回值  
 如果 `Left` 和 `Right` 表示具有相同长度的时间间隔，则第一个函数将返回 `true`。 否则，该函数返回 `false`。  
  
 如果 `Left` 和 `Right` 表示相同时间点，则第二个函数将返回 `true`。 否则，该函数返回 `false`。  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否大于另一个 `duration` 或 `time_point` 对象。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
### <a name="return-value"></a>返回值  
 每个函数均返回 `Right < Left`。  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否大于或等于另一个 `duration` 或 `time_point` 对象。  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左侧的 `duration` 或 `time_point` 对象。  
  
 `Right`  
 右侧的 `duration` 或 `time_point` 对象。  
  
### <a name="return-value"></a>返回值  
 每个函数均返回 `!(Left < Right)`。  
  
##  <a name="a-nameoperatormoduloa--operator-modulo"></a><a name="operator_modulo"></a>  operator modulo  
 用于对 [duration](../standard-library/duration-class.md) 对象进行取模操作的运算符。  
  
```  
template <class Rep1, class Period1, class Rep2>  
constexpr duration<Rep1, Period1, Rep2>::type 
   operator%(
      const duration<Rep1, Period1>& Dur,  
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,  
     const duration<Rep2, Period2>& Right);
```  
  
### <a name="parameters"></a>参数  
 `Dur`  
 一个 `duration` 对象。  
  
 `Div`  
 一个整数值。  
  
 `Left`  
 左 `duration` 对象。  
  
 `Right`  
 正确的 `duration` 对象。  
  
### <a name="return-value"></a>返回值  
 第一个函数返回 `duration` 对象，其间隔长度是 `Dur` 取模 `Div`。  
  
 第二个函数返回一个值，该值表示 `Left` 取模 `Right`。  
  
## <a name="see-also"></a>另请参阅  
 [\<chrono>](../standard-library/chrono.md)


