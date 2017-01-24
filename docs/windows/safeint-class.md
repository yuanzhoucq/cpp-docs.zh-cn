---
title: "SafeInt 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeInt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeInt 类"
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
caps.latest.revision: 16
caps.handback.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

扩展整数基元防止整数溢出和比较不同类型的整数。  
  
## 语法  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### 参数  
  
|模板|说明|  
|--------|--------|  
|T|`SafeInt` 替换整数或布尔参数的类型。|  
|E|定义错误处理策略的枚举数据类型。|  
|U|整数或布尔参数类型的附属操作数。|  
  
|参数|说明|  
|--------|--------|  
|\[in\] rhs|输入参数由多个独立函数的运算符右侧的值表示。|  
|\[in\] i|输入参数由多个独立函数的运算符右侧的值表示。|  
|\[in\] bits|输入参数由多个独立函数的运算符右侧的值表示。|  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|默认构造函数。|  
  
### 赋值运算符  
  
|Name|语法|  
|----------|--------|  
|\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|\=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|\=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### 强制转换运算符  
  
|Name|语法|  
|----------|--------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|\_\_int16|`operator __int16() const`|  
|unsigned \_\_int16|`operator unsigned __int16() const`|  
|\_\_int32|`operator __int32() const`|  
|unsigned \_\_int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|\_\_int64|`operator __int64() const`|  
|unsigned \_\_int64|`operator unsigned __int64() const`|  
|wchar\_t|`operator wchar_t() const`|  
  
### 比较运算符  
  
|Name|语法|  
|----------|--------|  
|\<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|\<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|\>\=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|\>\=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|\>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|\>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|\<\=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|\<\=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|\=\=|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|\=\=|`bool operator== (bool rhs) const throw()`|  
|\=\=|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|\!\=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|\!\=|`bool operator!= (bool b) const throw()`|  
|\!\=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### 算术运算符  
  
|Name|语法|  
|----------|--------|  
|\+|`const SafeInt<T,E>& operator+ () const throw()`|  
|\-|`SafeInt<T,E> operator- () const`|  
|\+\+|`SafeInt<T,E>& operator++ ()`|  
|\-\-|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|\*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|\*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|\*\=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|\*\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|\*\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|\/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|\/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|\/\=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|\/\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|\/\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|\+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|\+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|\+\=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|\+\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|\+\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|\-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|\-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|\-\=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|\-\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|\-\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### 逻辑运算符  
  
|Name|语法|  
|----------|--------|  
|\!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|\<\<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|\<\<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|\<\<\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|\<\<\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|\>\>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|\>\>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|\>\>\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|\>\>\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&\=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^\=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;\=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## 备注  
 `SafeInt` 类可防止整数在数学运算溢出。  例如，假设添加了2个 8 位整数：一个值为 200，第二个值 100。  正确的数学运算是 200 \+ 100 \= 300。  但是，因为 8 位整数限制，最高为会丢失位，编译器将返回 44 \(300 \- 2<sup>8</sup>\)作为结果。  依赖此数学等式的所有操作生成意外行为。  
  
 `SafeInt` 类检查是否出现算术溢出或尝试被零除。  在这两种情况下，类调用错误处理程序对潜在问题进行警告。  
  
 只要它们是 `SafeInt` 对象，此类也可比较两种不同类型的整数。  通常，当您执行其中一个比较时，必须首先将数字转换为同一类型。  将数字转换为其他类型通常需要检查，以确保不丢失数据。  
  
 本主题列出运算符表和 `SafeInt`类支持的比较运算符。  大多数数学运算符返回 `T`类型的 `SafeInt` 对象。  
  
 在 `SafeInt` 和整型之间的比较操作可以在任一方向运行。  例如，`SafeInt<int>(x) < y` 和 `y > SafeInt<int>(x)` 有效，并返回相同的结果。  
  
 许多二元运算符不支持使用两个不同 `SafeInt` 类型。  这是 `&` 运算符的一个示例。  支持`SafeInt<T, E> & int`，但是， 不支持`SafeInt<T, E> & SafeInt<U, E>`。  在后面的示例中，编译器不知道返回什么类型的参数。  该问题的解决方案会将第二个参数转换回基类型。  通过使用这些参数，可以通过`SafeInt<T, E> & (U)SafeInt<U, E>`执行。  
  
> [!NOTE]
>  对于所有位运算，两个参数应是相同的大小。  如果大小不同，则编译器会引发[ASSERT](../Topic/ASSERT%20\(MFC\).md)异常。  此操作的结果不能保证准确。  若要解决此问题，请在转换较小的参数，直到大小与较大的参数相同。  
  
 对于shift运算符，移动的位多于模板类型将抛出断言异常。  这在发布模式下没有效果。  因为返回类型与基元类型相同，所以混合 SafeInt 参数的两种类型是可能的。  运算符右侧的数字仅指示要移动位的数目。  
  
 当运行一个SafeInt 对象的逻辑比较时，比较是强算术的。  例如，请考虑以下表达式：  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 第一个语句将解析为 `true`，而第二个语句将解析为 `false`。  0按位非是 0xFFFFFFFF。  在第二个语句中，默认比较运算符比较0xFFFFFFFF 和 0xFFFFFFFF 且认为它们相等。  `SafeInt`类的比较运算符注意第二个参数是负值，而第一个是无符号的。  因此，尽管位表示相同，`SafeInt` 逻辑运算符也意识到无符号整数大于 \-1。  
  
 当`?:` 三元运算符与`SafeInt` 类一起使用时要小心。  请考虑以下的代码行。  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 编译器无法将它转换为：  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 如果 `flag` 为 `false`，编译器引发异常而不是指派值 \-1 给 `x`。  因此，避免此行为，采取下行正确代码。  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` 和 `U` 可以分配布尔类型、字符类型或整数类型。  整型可以是带符号或无符号的 8 位到 64 位的任何范围。  
  
> [!NOTE]
>  尽管 `SafeInt` 类接受任意整数，但它执行无符号类型更有效。  
  
 `E` 是 `SafeInt` 使用的错误处理机制。   SafeInt 库提供两个错误处理机制。  默认策略是 `SafeIntErrorPolicy_SafeIntException`，发生错误时,则引发 [SafeIntException 类](../windows/safeintexception-class.md)异常。  其他策略为 `SafeIntErrorPolicy_InvalidParameter`，如果出错,则停止程序。  
  
 自定义错误策略的两个选项。  在创建 `SafeInt`时，第一种选择是设置参数 `E`。  如果要更改`SafeInt`的错误处理策略，请使用此选项。  另一种选择是在包含 `SafeInt` 库中之前，定义 `_SAFEINT_DEFAULT_ERROR_POLICY` 为自定义错误处理类。  如果要为代码中的`SafeInt` 类的所有实例更改默认错误处理策略，则使用此选项。  
  
> [!NOTE]
>  处理来自 SafeInt 库的错误的自定义的类不应返回错误处理程序的代码的控件。  在调用错误处理程序后，`SafeInt` 运算的结果都不可信任。  
  
## 要求  
 **页眉:** safeint.h  
  
 **命名空间：** msl::utilities  
  
## 请参阅  
 [其他支持库类](http://msdn.microsoft.com/zh-cn/406fd46e-d53f-4096-ab40-36aa754c7a5c)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)