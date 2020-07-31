---
title: SafeInt 类
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: 97d81401cfd01d6d39457a9d63c39bc25901128e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219347"
---
# <a name="safeint-class"></a>SafeInt 类

扩展整数基元，有助于防止整数溢出，并便于比较不同类型的整数。

> [!NOTE]
> 最新版本的 SafeInt 库位于 [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) 。 若要使用 SafeInt 库，请克隆存储库，并`#include "SafeInt.hpp"`

## <a name="syntax"></a>语法

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>参数

| 模板  |  描述 |
|--------|------------|
| T         |  `SafeInt` 替换的整数或布尔参数的类型。 |
| E         |  定义错误处理策略的枚举数据类型。 |
| U         |  辅助操作数的整数或布尔参数的类型。 |

| 参数  |  描述 |
|---------|-----------------|
| rhs**      |  [输入] 输入参数，表示多个独立函数中的运算符的右侧值。 |
| *i*        |  [输入] 输入参数，表示多个独立函数中的运算符的右侧值。 |
| *带宽*     |  [输入] 输入参数，表示多个独立函数中的运算符的右侧值。 |

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

| “属性”                          |  描述 |
|---------------------------|--------------------|
| [SafeInt：： SafeInt](#safeint)  |  默认构造函数。 |

### <a name="assignment-operators"></a>赋值运算符

| 名称  |  语法 |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>强制转换运算符

| 名称              |  语法 |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| signed char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| unsigned __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| unsigned __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| unsigned __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>比较运算符

| 名称  |  语法 |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>算术运算符

| 名称  |  语法 |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>逻辑运算符

| 名称     |  语法 |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>备注

`SafeInt` 类可防止数学运算中出现整数溢出。 例如，假设将两个 8 位整数相加：一个值为 200，另一个值为 100。 正确的数学运算是 200 + 100 = 300。 不过，由于存在 8 位整数限制，因此高位会丢失，并且编译器返回 44 (300 - 2<sup>8</sup>) 作为结果。 任何依赖此数学等式的运算都会生成意外行为。

`SafeInt` 类检查是否发生算术溢出，或代码是否尝试除以零。 在这两种情况下，此类都会调用错误处理程序，以警告程序存在潜在问题。

此类还便于比较两个不同类型的整数，只要它们是 `SafeInt` 对象。 通常，在进行比较时，必须首先将数字转换为同一类型。 将一种类型的数字强制转换为另一种类型通常需要进行检查，以确保没有数据丢失。

本主题中的“运算符”表列出了 `SafeInt` 类支持的数学运算符和比较运算符。 大多数数学运算符返回类型为 `T` 的 `SafeInt` 对象。

`SafeInt` 和整型类型之间的比较运算可以在任意一个方向上执行。 例如，`SafeInt<int>(x) < y` 和 `y> SafeInt<int>(x)` 都是有效的，返回的结果也相同。

许多二进制运算符不支持使用两种不同 `SafeInt` 的类型。 其中一个例子就是 `&` 运算符。 `SafeInt<T, E> & int`支持，但 `SafeInt<T, E> & SafeInt<U, E>` 不支持。 在后一个示例中，编译器不知道返回什么类型的参数。 此问题的一个解决方案是，将第二个参数强制转换回基类型。 通过使用相同参数，可以借助 `SafeInt<T, E> & (U)SafeInt<U, E>` 完成此操作。

> [!NOTE]
> 对于任何位运算，两个不同的参数应大小相同。 如果大小不同，编译器便会抛出 [ASSERT](../mfc/reference/diagnostic-services.md#assert) 异常。 无法保证此操作的结果是准确的。 若要解决此问题，请强制转换较小的参数，直到其大小与较大参数相同。

对于移位运算符，如果移位位数超出模板类型的现有位数，便会抛出 ASSERT 异常。 这在发布模式下不会产生任何影响。 对于移位运算符，可以混用两种类型的 SafeInt 参数，因为返回类型与原始类型相同。 运算符右侧的数字仅指明要移位的位数。

使用 SafeInt 对象进行逻辑比较时，比较是严格的算法。 以下面这些表达式为例：

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

第一条语句解析为 **`true`** ，但第二条语句解析为 **`false`** 。 0 的按位求反结果为 0xFFFFFFFF。 在第二个语句中，默认比较运算符将 0xFFFFFFFF 与 0xFFFFFFFF 进行比较，并认为它们相等。 `SafeInt` 类的比较运算符了解到，第二个参数为负数，而第一个参数则无符号。 因此，尽管位表示形式完全相同，但 `SafeInt` 逻辑运算符了解到无符号整数大于 -1。

结合使用 `SafeInt` 类和 `?:` 三元运算符时要谨慎。 以下面的代码行为例。

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

编译器将它转换为：

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

如果 `flag` 为 **`false`** ，则编译器会引发异常，而不是将值-1 赋给 `x` 。 因此，为了避免此行为，请使用如下正确的代码行。

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` 和 `U` 可以分配有布尔类型、字符类型或整数类型。 整数类型可以有符号，也可以无符号，且大小介于 8 位和 64 位之间。

> [!NOTE]
> 尽管 `SafeInt` 类接受任何类型的整数，但它对无符号类型的执行效率更高。

`E` 是 `SafeInt` 使用的错误处理机制。 SafeInt 库随附了两个错误处理机制。 默认策略是 `SafeIntErrorPolicy_SafeIntException`，它在出错时抛出 [SafeIntException 类](safeintexception-class.md)异常。 另一个策略是 `SafeIntErrorPolicy_InvalidParameter`，它在出错时停止程序运行。

自定义错误策略的方法有两种。 第一种方法是，在创建 `SafeInt` 时设置参数 `E`。 如果只想更改一个 `SafeInt` 的错误处理策略，请使用这种方法。 另一种方法是，在添加 `SafeInt` 库前，将 _SAFEINT_DEFAULT_ERROR_POLICY 定义为自定义错误处理类。 若要对代码中 `SafeInt` 类的所有实例更改默认错误处理策略，请使用这种方法。

> [!NOTE]
> 处理 SafeInt 库中错误的自定义类不得将控制权返回给调用了错误处理程序的代码。 调用错误处理程序后，操作的结果将 `SafeInt` 不受信任。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SafeInt`

## <a name="requirements"></a>要求

**标头：** SafeInt. hpp
> [!NOTE]
> 此库的最新版本位于 [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) 。 克隆库，并包括 SafeInt hpp 以使用 SafeInt 库。
> 首选此 github 存储库 <safeint>。 它是 <safeint> 的新式版本，其中包括少量的 bug 修复，使用 c + + 的新式功能生成更高效的代码，并可移植到使用 gcc、clang 或 Intel 编译器的任何平台。

### <a name="example"></a>示例

```c
#include "SafeInt.hpp" // set path to your clone of the SafeInt GitHub repo (https://github.com/dcleblanc/SafeInt)

int main()
{
    int divisor = 3;
    int dividend = 6;
    int result;

    bool success = SafeDivide(dividend, divisor, result); // result = 2
    success = SafeDivide(dividend, 0, result); // expect fail. result isn't modified.
}
```

**命名空间：** 无

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt：： SafeInt

构造 `SafeInt` 对象。

```cpp
SafeInt() throw

SafeInt (const T& i) throw ()

SafeInt (bool b) throw ()

template <typename U>
SafeInt (const SafeInt <U, E>& u)

I template <typename U>
SafeInt (const U& i)
```

### <a name="parameters"></a>参数

`i`<br/>
[输入] 新 `SafeInt` 对象的值。 这必须是 T 或 U 类型的参数，具体视构造函数而定。

`b`<br/>
[输入] 新 `SafeInt` 对象的布尔值。

`u`<br/>
[输入] U 类型的 `SafeInt`。新 `SafeInt` 对象的值与 u** 相同，但类型为 T。

`U`存储在中的数据的类型 `SafeInt` 。 这可以是布尔类型、字符类型或整数类型。 如果它是整数类型，它可以是有符号或无符号的，并且可以介于8到64位之间。

### <a name="remarks"></a>备注

构造函数的输入参数 i** 或 u** 必须是布尔类型、字符类型或整数类型。 如果它是另一种类型的参数， `SafeInt` 类将调用[static_assert](../cpp/static-assert.md)以指示无效的输入参数。

使用模板类型 `U` 的构造函数自动将输入参数转换为 `T` 指定的类型。 `SafeInt` 类转换数据，而不会有任何数据丢失。 `E`如果无法在 `T` 不丢失数据的情况下将数据转换为类型，它将报告错误处理程序。

如果是通过布尔参数创建 `SafeInt`，需要立即初始化值。 不能 `SafeInt` 使用代码构造 `SafeInt<bool> sb;` 。 这会生成编译错误。
