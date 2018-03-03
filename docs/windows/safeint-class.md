---
title: "SafeInt 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea076ea092257fd5bf6acd6d597f79ef42dd96f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="safeint-class"></a>SafeInt 类
扩展来帮助防止整数溢出的整数基元，并可用于比较不同类型的整数。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### <a name="parameters"></a>参数  
  
|模板|描述|  
|--------------|-----------------|  
|T|类型为整数或布尔型参数，`SafeInt`替换。|  
|E|枚举的数据类型定义的错误处理策略。|  
|U|整数或布尔参数的辅助操作数的类型。|  
  
|参数|描述|  
|---------------|-----------------|  
|[] in rhs|输入的参数表示多个独立的函数中的运算符右侧的值。|  
|[in] 我|输入的参数表示多个独立的函数中的运算符右侧的值。|  
|[] in bits|输入的参数表示多个独立的函数中的运算符右侧的值。|  
  
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
 `SafeInt`类可防止在数学运算的整数溢出。 例如，考虑添加两个 8 位整数： 一个具有值为 200，第二个具有值为 100。 正确的数学运算将 200 + 100 = 300。 但是，由于的 8 位整数限制，上部位都将丢失，而编译器将返回 44 (300 2<sup>8</sup>) 作为结果。 依赖于此数学公式的任何操作将生成意外的行为。  
  
 `SafeInt`类将检查是否发生算术溢出时，或是否该代码尝试除以零。 在这两种情况下，类调用错误处理程序潜在问题的程序，则发出警告。  
  
 此类，您还可以比较两个不同类型的整数，只要它们是`SafeInt`对象。 通常情况下，在执行比较时，您必须首先将的编号，以相同的类型。 强制转换到另一种类型的一个数字通常需要检查以确保不会丢失数据。  
  
 本主题中的运算符表列出支持的数学和比较运算符`SafeInt`类。 大多数的数学运算符将返回`SafeInt`类型的对象`T`。  
  
 之间的比较运算`SafeInt`，并且可以在任一方向执行整数类型。 例如，`SafeInt<int>(x) < y`和`y > SafeInt<int>(x)`有效并将返回相同的结果。  
  
 很多二元运算符不支持使用两个不同`SafeInt`类型。 这一个示例是`&`运算符。 `SafeInt<T, E> & int`支持，但`SafeInt<T, E> & SafeInt<U, E>`不是。 在后一种的示例中，编译器不知道哪种类型的参数返回。 此问题的一种解决方案是强制转换回的基类型的第二个参数。 通过使用相同的参数，这可通过`SafeInt<T, E> & (U)SafeInt<U, E>`。  
  
> [!NOTE]
>  对于任何按位运算，两个不同的参数应该是相同的大小。 如果大小不同，编译器将引发[断言](../mfc/reference/diagnostic-services.md#assert)异常。 此操作的结果不能保证不准确。 若要解决此问题，将参数强制转换较小之前更大的参数相同的大小。  
  
 移位运算符，为转换不是模板类型存在的更多比特将引发断言异常。 在发布模式下，这将产生任何影响。 混合使用两种类型的 SafeInt 参数是可能移位运算符，因为返回类型是原始类型相同。 运算符右侧数仅指示要位移位数的数。  
  
 当你执行与 SafeInt 对象的逻辑比较时，比较将为严格算术型。 例如，考虑这些表达式：  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 第一个语句解析为`true`，但第二个语句解析为`false`。 0 的按位求反为 0xFFFFFFFF。 在第二个语句中，默认的比较运算符比较 0xFFFFFFFF 到 0xFFFFFFFF，并将认为它们相等。 比较运算符中的`SafeInt`类意识到第二个参数是负数，而第一个参数是无符号。 因此，位表示形式相同，但`SafeInt`逻辑运算符意识到的无符号的整数大于-1。  
  
 请注意，当你使用`SafeInt`类连同`?:`三元运算符。 请考虑以下代码行。  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 编译器将其转换为此：  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 如果`flag`是`false`，编译器将引发异常而不是分配的值-1 到`x`。 因此，若要避免此行为，正确的代码以使用是以下行。  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T`和`U`布尔值类型、 字符类型或整型可以分配。 类型可以有符号或无符号的整数部分和任何大小从 8 位到 64 位。  
  
> [!NOTE]
>  尽管`SafeInt`类接受任何类型的整数，它更有效地执行与无符号类型。  
  
 `E`是错误处理机制的`SafeInt`使用。 SafeInt 库提供了两个错误处理机制。 默认策略是`SafeIntErrorPolicy_SafeIntException`，该类会引发[SafeIntException 类](../windows/safeintexception-class.md)异常时发生错误。 其他策略`SafeIntErrorPolicy_InvalidParameter`，这在出错时停止该程序。  
  
 有两个选项，以自定义错误策略。 第一个选项是将参数设置`E`创建时`SafeInt`。 使用此选项，当你想要更改的错误处理策略，仅针对之一`SafeInt`。 另一个选项是定义`_SAFEINT_DEFAULT_ERROR_POLICY`是您自定义的错误处理类，包括在内时`SafeInt`库。 如果你想要更改默认的错误处理策略的所有实例使用此选项`SafeInt`在代码中的类。  
  
> [!NOTE]
>  处理错误 SafeInt 库中的自定义的类应将控制权返回到调用错误处理程序的代码。 调用错误处理程序时，结果后`SafeInt`操作不能为受信任。  
  
## <a name="requirements"></a>惠?  
 **标头：** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)