---
title: SafeInt 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1e4ac8898b48c4b64d0b12b945ab45b1c5f1436
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606151"
---
# <a name="safeint-class"></a>SafeInt 类
扩展的整数基元来帮助防止整数溢出，并可用于比较不同类型的整数。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
### <a name="parameters"></a>参数  
  
|模板|描述|  
|--------------|-----------------|  
|T|类型为整数或布尔参数的**SafeInt**替换。|  
|E|定义的错误处理策略枚举的数据类型。|  
|U|整数或布尔参数的辅助操作数的类型。|  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*rhs*|输入的参数，表示多个独立函数中的运算符右侧的值。|  
|[in]*我*|输入的参数，表示多个独立函数中的运算符右侧的值。|  
|[in]*bits*|输入的参数，表示多个独立函数中的运算符右侧的值。|  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|默认构造函数。|  
  
### <a name="assignment-operators"></a>赋值运算符  
  
|name|语法|  
|----------|------------|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### <a name="casting-operators"></a>强制转换运算符  
  
|name|语法|  
|----------|------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|__int16|`operator __int16() const`|  
|unsigned __int16|`operator unsigned __int16() const`|  
|__int32|`operator __int32() const`|  
|unsigned __int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|__int64|`operator __int64() const`|  
|unsigned __int64|`operator unsigned __int64() const`|  
|wchar_t|`operator wchar_t() const`|  
  
### <a name="comparison-operators"></a>比较运算符  
  
|name|语法|  
|----------|------------|  
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|==|`bool operator== (bool rhs) const throw()`|  
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|!=|`bool operator!= (bool b) const throw()`|  
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### <a name="arithmetic-operators"></a>算术运算符  
  
|name|语法|  
|----------|------------|  
|+|`const SafeInt<T,E>& operator+ () const throw()`|  
|-|`SafeInt<T,E> operator- () const`|  
|++|`SafeInt<T,E>& operator++ ()`|  
|--|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### <a name="logical-operators"></a>逻辑运算符  
  
|name|语法|  
|----------|------------|  
|!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## <a name="remarks"></a>备注  
 **SafeInt**类可防止整数溢出数学运算。 例如，考虑添加两个 8 位整数： 其中一个的值为 200，第二个值为 100。 正确的数学运算是 200 + 100 = 300。 但是，由于的 8 位整数限制，上限的位将会丢失，并且编译器将返回 44 (300 2<sup>8</sup>) 作为结果。 任何操作都取决于此数学等式将生成意外的行为。  
  
 **SafeInt**类检查是否发生算术溢出时，或者是否该代码尝试除以零。 在这两种情况下，类会调用错误处理程序的潜在问题的程序，则发出警告。  
  
 此类，您还可以比较两个不同类型的整数，前提是它们**SafeInt**对象。 通常情况下，当执行比较，您首先必须将相同类型的数字。 强制转换到另一种类型的一个数通常需要检查以确保不会丢失数据。  
  
 本主题中的运算符表列出了支持的数学和比较运算符**SafeInt**类。 大多数的数学运算符返回**SafeInt**类型的对象`T`。  
  
 之间的比较运算**SafeInt** ，可以在任一方向执行一种整型类型。 例如，同时`SafeInt<int>(x) < y`和`y> SafeInt<int>(x)`有效，并将返回相同的结果。  
  
 很多二元运算符不支持使用两个不同**SafeInt**类型。 一个示例是`&`运算符。 `SafeInt<T, E> & int` 受支持，但`SafeInt<T, E> & SafeInt<U, E>`不是。 在后一种示例中，编译器不知道哪种类型的参数返回。 此问题的一种解决方案是强制转换为基的类型的第二个参数。 通过使用相同的参数，这可以与`SafeInt<T, E> & (U)SafeInt<U, E>`。  
  
> [!NOTE]
>  对于任何按位运算，两个不同的参数应该是相同的大小。 如果大小不同，编译器将引发[ASSERT](../mfc/reference/diagnostic-services.md#assert)异常。 要准确，不能保证此操作的结果。 若要解决此问题，较小参数强制转换之前它是更大的参数具有相同的大小。  
  
 移位运算符，为转换为模板类型存在超出的位数将引发断言异常。 这不会影响在发布模式下。 混合使用两种类型的 SafeInt 参数是移位运算符有可能，因为返回类型是原始类型相同。 运算符右侧数仅指示移动位数的数。  
  
 当您执行与 SafeInt 对象的逻辑比较时，比较不严格算术。 例如，考虑两个表达式：  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 第一条语句解析为 **，则返回 true**，但第二个语句解析为**false**。 按位求反的 0 为 0xFFFFFFFF。 在第二个语句中，默认的比较运算符比较 0xFFFFFFFF 为 0xFFFFFFFF，并将认为它们相等。 比较运算符中的**SafeInt**类意识到第二个参数是负数，而第一个参数是无符号。 因此，位表示形式是相同的尽管**SafeInt**逻辑运算符意识到无符号的整数是否大于-1。  
  
 当你使用时要小心**SafeInt**类一起使用`?:`三元运算符。 请考虑以下代码行。  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 编译器将其转换为此：  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 如果`flag`是**false**，编译器将引发异常而不是分配的值-1 到`x`。 因此，若要避免此行为，要使用的正确代码是以下行。  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` 和`U`布尔值类型、 字符类型或整数类型可以分配。 类型可以有符号或无符号的整数部分和任何大小从 8 位到 64 位。  
  
> [!NOTE]
>  尽管**SafeInt**类接受任何类型的整数，它将处理无符号类型更高效地执行。  
  
 `E` 是错误处理机制的**SafeInt**使用。 SafeInt 库提供了两个错误处理机制。 默认策略是`SafeIntErrorPolicy_SafeIntException`，该类会引发[SafeIntException 类](../windows/safeintexception-class.md)发生错误时的异常。 另一个策略是`SafeIntErrorPolicy_InvalidParameter`，后者会停止该程序，如果发生错误。  
  
 有两个选项以自定义错误策略。 第一个选项是将参数设置`E`在创建时**SafeInt**。 使用此选项，当你想要更改的错误处理策略，仅针对之一**SafeInt**。 另一个选项是定义为自定义的错误处理类包含之前的 _SAFEINT_DEFAULT_ERROR_POLICY **SafeInt**库。 如果你想要更改默认错误处理策略的所有实例使用此选项**SafeInt**在代码中的类。  
  
> [!NOTE]
>  处理错误 SafeInt 库中的自定义的类应将控制返回给调用错误处理程序的代码。 错误处理程序调用的结果后**SafeInt**操作不能为受信任。  
  
## <a name="requirements"></a>要求  
 **标头：** safeint.h  
  
 **Namespace:** msl:: utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)