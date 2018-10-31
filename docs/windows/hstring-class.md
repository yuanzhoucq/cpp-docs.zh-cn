---
title: HString 类 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8165a404924b997d70d0097c28ac7d34ade92fc3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063856"
---
# <a name="hstring-class"></a>HString 类

用于管理的生命周期的帮助器类[HSTRING](/windows/desktop/WinRT/hstring)使用 RAII 模式。

## <a name="syntax"></a>语法

```cpp
class HString;
```

## <a name="remarks"></a>备注

Windows 运行时提供通过字符串的访问权限[HSTRING](/windows/desktop/WinRT/hstring)句柄。 `HString`类提供便利函数和运算符以简化使用 HSTRING 句柄。 此类可以处理它拥有通过 RAII 模式在 HSTRING 的生存期。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                | 描述
----------------------------------- | -----------------------------------------------------
[Hstring:: Hstring](#hstring)        | 初始化 `HString` 类的新实例。
[HString:: ~ HString](#tilde-hstring) | 销毁的当前实例`HString`类。

### <a name="public-methods"></a>公共方法

名称                                     | 描述
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Hstring:: Attach](#attach)               | 将指定相关联`HString`与当前对象`HString`对象。
[Hstring:: Copyto](#copyto)               | 复制当前`HString`到 HSTRING 对象的对象。
[Hstring:: Detach](#detach)               | 取消关联指定`HString`从其基础值的对象。
[Hstring:: Get](#get)                     | 检索基础 HSTRING 句柄的值。
[Hstring:: Getaddressof](#getaddressof)   | 检索指向基础 HSTRING 句柄。
[Hstring:: Isvalid](#isvalid)             | 指示是否当前`HString`对象是否有效。
[Hstring:: Makereference](#makereference) | 创建`HStringReference`从指定的字符串参数的对象。
[Hstring:: Release](#release)             | 删除基础字符串值，并初始化当前`HString`对象为空值。
[Hstring:: Set](#set)                     | 设置的当前值`HString`为指定的宽字符字符串的对象或`HString`参数。

### <a name="public-operators"></a>公共运算符

名称                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------
[Hstring:: Operator =](#operator-assign)       | 另一个的值移`HString`对象与当前`HString`对象。
[Hstring:: Operator = =](#operator-equality)    | 指示两个参数是否相等。
[Hstring:: Operator ！ =](#operator-inequality)  | 指示两个参数是否不相等。
[Hstring:: Operator&lt;](#operator-less-than) | 指示第一个参数是否小于第二个参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HString`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

销毁的当前实例`HString`类。

```cpp
~HString() throw()
```

## <a name="attach"></a>Hstring:: Attach

将指定相关联`HString`与当前对象`HString`对象。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>参数

*hstr*<br/>
一个现有的 `HString` 对象。

## <a name="copyto"></a>Hstring:: Copyto

复制当前`HString`到 HSTRING 对象的对象。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*str*<br/>
接收副本的 HSTRING。

### <a name="remarks"></a>备注

此方法调用[WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx)函数。

## <a name="detach"></a>Hstring:: Detach

取消关联指定`HString`从其基础值的对象。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>返回值

基础`HString`分离操作启动之前的值。

## <a name="get"></a>Hstring:: Get

检索基础 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>返回值

基础 HSTRING 句柄的值

## <a name="getaddressof"></a>Hstring:: Getaddressof

检索指向基础 HSTRING 句柄。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>返回值

指向基础 HSTRING 句柄的指针。

### <a name="remarks"></a>备注

此操作后，将销毁基础 HSTRING 句柄的字符串值。

## <a name="hstring"></a>Hstring:: Hstring

初始化 `HString` 类的新实例。

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>参数

*hstr*<br/>
HSTRING 句柄。

*other*<br/>
一个现有的 `HString` 对象。

### <a name="remarks"></a>备注

第一个构造函数初始化新`HString`对象为空。

第二个构造函数初始化新`HString`对象的现有值与*其他*参数，然后再销毁*其他*参数。

## <a name="isvalid"></a>Hstring:: Isvalid

指示是否当前`HString`对象是否为空。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>参数

**true**如果当前`HString`对象不为空; 否则为**false**。

## <a name="makereference"></a>Hstring:: Makereference

创建`HStringReference`从指定的字符串参数的对象。

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>参数

*sizeDest*<br/>
一个模板参数，指定的目标大小`HStringReference`缓冲区。

*str*<br/>
对宽字符串的引用。

len<br/>
最大长度*str*要在此操作中使用的参数缓冲区。 如果*len*参数未指定，整个*str*使用参数。

### <a name="return-value"></a>返回值

`HStringReference`对象，其值为与指定相同*str*参数。

## <a name="operator-assign"></a>Hstring:: Operator = 运算符

另一个的值移`HString`对象与当前`HString`对象。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>参数

*other*<br/>
一个现有的 `HString` 对象。

### <a name="remarks"></a>备注

现有值*其他*对象复制到当前`HString`对象，然后*其他*对象被销毁。

## <a name="operator-equality"></a>Hstring:: Operator = = 运算符

指示两个参数是否相等。

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是`HString`或`HStringReference`对象或 HSTRING 句柄。

*rhs*<br/>
要比较的第二个参数。*rhs*可以是`HString`或`HStringReference`对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

**true**如果*lhs*并*rhs*参数不相等; 否则为**false**。

## <a name="operator-inequality"></a>Hstring:: Operator ！ = 运算符

指示两个参数是否不相等。

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是`HString`或`HStringReference`对象或 HSTRING 句柄。

*rhs*<br/>
要比较的第二个参数。*rhs*可以是`HString`或`HStringReference`对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

**true**如果*lhs*并*rhs*参数是否不相等; 否则为**false**。

## <a name="operator-less-than"></a>Hstring:: Operator&lt;运算符

指示第一个参数是否小于第二个参数。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是对引用`HString`。

*rhs*<br/>
要比较的第二个参数。 *rhs*可以是对引用`HString`。

### <a name="return-value"></a>返回值

**true**如果*lhs*参数是小于*rhs*参数; 否则为**false**。

## <a name="release"></a>Hstring:: Release

删除基础字符串值，并初始化当前`HString`对象为空值。

```cpp
void Release() throw()
```

## <a name="set"></a>Hstring:: Set

设置的当前值`HString`为指定的宽字符字符串的对象或`HString`参数。

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>参数

*str*<br/>
宽字符字符串。

len<br/>
最大长度*str*分配给当前的参数`HString`对象。

*hstr*<br/>
一个现有的 `HString` 对象。
