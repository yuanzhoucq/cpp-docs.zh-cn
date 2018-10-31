---
title: SafeInt 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7d9c6b68f67185bb9cc529949fcc7c43e91d21e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081857"
---
# <a name="safeint-class"></a>SafeInt 类

扩展的整数基元来帮助防止整数溢出，并可用于比较不同类型的整数。

> [!NOTE] 
> 此库的最新版本位于[ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt)。

## <a name="syntax"></a>语法

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>参数

模板 | 描述
-------- | -------------------------------------------------------------------
T        | 类型为整数或布尔参数的`SafeInt`替换。
E        | 定义的错误处理策略枚举的数据类型。
U        | 整数或布尔参数的辅助操作数的类型。

参数 | 描述
--------- | ---------------------------------------------------------------------------------------------------------------------
*rhs*     | [in]输入的参数，表示多个独立函数中的运算符右侧的值。
*i*       | [in]输入的参数，表示多个独立函数中的运算符右侧的值。
*Bits*    | [in]输入的参数，表示多个独立函数中的运算符右侧的值。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                         | 描述
---------------------------- | --------------------
[SafeInt::SafeInt](#safeint) | 默认构造函数。

### <a name="assignment-operators"></a>赋值运算符

name | 语法
---- | ---------------------------------------------------------------------------------------
=    | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`
=    | `SafeInt<T,E>& operator= (const T& rhs) throw()`
=    | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`
=    | `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`

### <a name="casting-operators"></a>强制转换运算符

name             | 语法
---------------- | -----------------------------------
bool             | `operator bool() throw()`
char             | `operator char() const`
signed char      | `operator signed char() const`
unsigned char    | `operator unsigned char() const`
__int16          | `operator __int16() const`
unsigned __int16 | `operator unsigned __int16() const`
__int32          | `operator __int32() const`
unsigned __int32 | `operator unsigned __int32() const`
long             | `operator long() const`
unsigned long    | `operator unsigned long() const`
__int64          | `operator __int64() const`
unsigned __int64 | `operator unsigned __int64() const`
wchar_t          | `operator wchar_t() const`

### <a name="comparison-operators"></a>比较运算符

name | 语法
---- | --------------------------------------------------------------------------
<    | `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`
<    | `bool operator< (SafeInt<T,E> rhs) const throw()`
>=   | `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`
>=   | `Bool operator>= (SafeInt<T,E> rhs) const throw()`
>    | `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`
>    | `Bool operator> (SafeInt<T,E> rhs) const throw()`
<=   | `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`
<=   | `bool operator<= (SafeInt<T,E> rhs) const throw()`
==   | `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`
==   | `bool operator== (bool rhs) const throw()`
==   | `bool operator== (SafeInt<T,E> rhs) const throw()`
!=   | `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`
!=   | `bool operator!= (bool b) const throw()`
!=   | `bool operator!= (SafeInt<T,E> rhs) const throw()`

### <a name="arithmetic-operators"></a>算术运算符

name | 语法
---- | ---------------------------------------------------------------------------------
+    | `const SafeInt<T,E>& operator+ () const throw()`
-    | `SafeInt<T,E> operator- () const`
++   | `SafeInt<T,E>& operator++ ()`
--   | `SafeInt<T,E>& operator-- ()`
%    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`
%    | `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`
%=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`
%=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`
*    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`
*    | `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`
*=   | `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`
*=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`
*=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`
/    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`
/    | `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`
/=   | `SafeInt<T,E>& operator/= (SafeInt<T,E> i)`
/=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`
/=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`
+    | `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`
+    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`
+=   | `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`
+=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`
+=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`
-    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`
-    | `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`
-=   | `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`
-=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`
-=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`

### <a name="logical-operators"></a>逻辑运算符

name    | 语法
------- | -----------------------------------------------------------------------------------------------
!       | `bool operator !() const throw()`
~       | `SafeInt<T,E> operator~ () const throw()`
<<      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`
<<      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`
<<=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`
<<=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`
>>      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`
>>      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`
>>=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`
>>=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`
&       | `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`
&       | `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`
&=      | `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`
&=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`
&=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`
^       | `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`
^       | `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`
^=      | `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`
^=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`
^=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`
&#124;  | `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`
&#124;  | `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`
&#124;= | `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`
&#124;= | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`
&#124;= | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`

## <a name="remarks"></a>备注

`SafeInt`类可防止整数溢出数学运算。 例如，考虑添加两个 8 位整数： 其中一个的值为 200，第二个值为 100。 正确的数学运算是 200 + 100 = 300。 但是，由于的 8 位整数限制，上限的位将会丢失，并且编译器将返回 44 (300 2<sup>8</sup>) 作为结果。 任何操作都取决于此数学等式将生成意外的行为。

`SafeInt`类检查是否发生算术溢出时，或者是否该代码尝试除以零。 在这两种情况下，类会调用错误处理程序的潜在问题的程序，则发出警告。

此类还可用于比较两个不同类型的整数，只要它们是`SafeInt`对象。 通常情况下，当执行比较，您首先必须将相同类型的数字。 强制转换到另一种类型的一个数通常需要检查以确保不会丢失数据。

本主题中的运算符表列出了支持的数学和比较运算符`SafeInt`类。 大多数的数学运算符返回`SafeInt`类型的对象`T`。

之间的比较操作`SafeInt`，可以在任一方向执行一种整型类型。 例如，同时`SafeInt<int>(x) < y`和`y> SafeInt<int>(x)`有效，并将返回相同的结果。

很多二元运算符不支持使用两个不同`SafeInt`类型。 一个示例是`&`运算符。 `SafeInt<T, E> & int` 受支持，但`SafeInt<T, E> & SafeInt<U, E>`不是。 在后一种示例中，编译器不知道哪种类型的参数返回。 此问题的一种解决方案是强制转换为基的类型的第二个参数。 通过使用相同的参数，这可以与`SafeInt<T, E> & (U)SafeInt<U, E>`。

> [!NOTE]
> 对于任何按位运算，两个不同的参数应该是相同的大小。 如果大小不同，编译器将引发[ASSERT](../mfc/reference/diagnostic-services.md#assert)异常。 要准确，不能保证此操作的结果。 若要解决此问题，较小参数强制转换之前它是更大的参数具有相同的大小。

移位运算符，为转换为模板类型存在超出的位数将引发断言异常。 这不会影响在发布模式下。 混合使用两种类型的 SafeInt 参数是移位运算符有可能，因为返回类型是原始类型相同。 运算符右侧数仅指示移动位数的数。

当您执行与 SafeInt 对象的逻辑比较时，比较不严格算术。 例如，考虑两个表达式：

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

第一条语句解析为 **，则返回 true**，但第二个语句解析为`false`。 按位求反的 0 为 0xFFFFFFFF。 在第二个语句中，默认的比较运算符比较 0xFFFFFFFF 为 0xFFFFFFFF，并将认为它们相等。 比较运算符中的`SafeInt`类意识到第二个参数是负数，而第一个参数是无符号。 因此，尽管位表示形式是相同的`SafeInt`逻辑运算符意识到无符号的整数是否大于-1。

当你使用时要小心`SafeInt`类一起使用`?:`三元运算符。 请考虑以下代码行。

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

编译器将其转换为此：

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

如果`flag`是`false`，编译器将引发异常而不是分配的值-1 到`x`。 因此，若要避免此行为，要使用的正确代码是以下行。

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` 和`U`布尔值类型、 字符类型或整数类型可以分配。 类型可以有符号或无符号的整数部分和任何大小从 8 位到 64 位。

> [!NOTE]
> 尽管`SafeInt`类接受任何类型的整数，它将处理无符号类型更高效地执行。

`E` 是错误处理机制的`SafeInt`使用。 SafeInt 库提供了两个错误处理机制。 默认策略是`SafeIntErrorPolicy_SafeIntException`，该类会引发[SafeIntException 类](../windows/safeintexception-class.md)发生错误时的异常。 另一个策略是`SafeIntErrorPolicy_InvalidParameter`，后者会停止该程序，如果发生错误。

有两个选项以自定义错误策略。 第一个选项是将参数设置`E`当你创建`SafeInt`。 如果你想要更改的错误处理策略，仅为其中一个使用此选项`SafeInt`。 另一个选项是定义 _SAFEINT_DEFAULT_ERROR_POLICY 包含之前为您的自定义的错误处理类`SafeInt`库。 如果你想要更改默认错误处理策略的所有实例使用此选项`SafeInt`在代码中的类。

> [!NOTE]
> 处理错误 SafeInt 库中的自定义的类应将控制返回给调用错误处理程序的代码。 错误处理程序调用的结果后`SafeInt`操作不能为受信任。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SafeInt`

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** msl:: utilities

## <a name="safeint"></a>Safeint:: Safeint

构造 `SafeInt` 对象。

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)
```

### <a name="parameters"></a>参数

*i*<br/>
[in]新值`SafeInt`对象。 这必须是类型 T 或 U，具体取决于构造函数的参数。

*b*<br/>
[in]新的布尔值`SafeInt`对象。

*u*<br/>
[in]一个`SafeInt`为类型 u。新`SafeInt`对象将具有相同的值*u*，但将类型为 t。

U 中存储的数据类型`SafeInt`。 这可以是一个布尔值、 字符或整数类型。 如果它是整数类型，可以对其签名或未签名且长度在 8 到 64 位之间。

### <a name="remarks"></a>备注

构造函数中，输入的参数*我*或*u*，必须为布尔值、 字符或整数类型。 如果它是另一种类型的参数，`SafeInt`类调用[static_assert](../cpp/static-assert.md)以指示输入的参数无效。

使用模板类型的构造函数`U`自动将输入的参数转换为指定的类型`T`。 `SafeInt`类将转换数据，而不丢失任何数据。 它报告给错误处理程序`E`不能转换为类型的数据如果`T`无数据丢失。

如果您创建`SafeInt`布尔参数，则需立即初始化的值。 无法构造`SafeInt`使用代码`SafeInt<bool> sb;`。 这将生成编译错误。
