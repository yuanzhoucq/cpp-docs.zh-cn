---
title: HString 类
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
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
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371435"
---
# <a name="hstring-class"></a>HString 类

使用 RAII 模式管理[HSTRING](/windows/win32/WinRT/hstring)的生存期的帮助器类。

## <a name="syntax"></a>语法

```cpp
class HString;
```

## <a name="remarks"></a>备注

Windows 运行时通过[HSTRING](/windows/win32/WinRT/hstring)句柄提供对字符串的访问。 该`HString`类提供方便的功能和运算符，以简化使用 HSTRING 句柄。 此类可以通过 RAII 模式处理它拥有的 HSTRING 的生存期。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                | 说明
----------------------------------- | -----------------------------------------------------
[HString：：HString](#hstring)        | 初始化 `HString` 类的新实例。
[HString：：*HString](#tilde-hstring) | 销毁`HString`类的当前实例。

### <a name="public-methods"></a>公共方法

名称                                     | 说明
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString：：附加](#attach)               | 将指定的`HString`对象与当前`HString`对象关联。
[HString::CopyTo](#copyto)               | 将当前`HString`对象复制到 HSTRING 对象。
[赫斯特林：:D塔奇](#detach)               | 取消指定`HString`对象与其基础值的关联。
[HString：获取](#get)                     | 检索基础 HSTRING 句柄的值。
[HString：获取地址](#getaddressof)   | 检索指向基础 HSTRING 句柄的指针。
[HString：：获取原始缓冲区](#getrawbuffer)   | 检索指向基础字符串数据的指针。
[HString：：有效](#isvalid)             | 指示当前`HString`对象是否有效。
[HString：：使参考](#makereference) | 从指定的`HStringReference`字符串参数创建对象。
[HString：：发布](#release)             | 删除基础字符串值并将当前`HString`对象归为空值。
[HString：：设置](#set)                     | 将当前`HString`对象的值设置到指定的宽字符字符串或`HString`参数。

### <a name="public-operators"></a>公共运算符

名称                                         | 说明
-------------------------------------------- | ----------------------------------------------------------------------------
[HString：：运算符*](#operator-assign)       | 将另一`HString`个对象的值移动到当前`HString`对象。
[HString：：运算符*](#operator-equality)    | 指示两个参数是否相等。
[HString：：操作员！](#operator-inequality)  | 指示两个参数是否不相等。
[HString：：运算符&lt;](#operator-less-than) | 指示第一个参数是否小于第二个参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HString`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString：：*HString

销毁`HString`类的当前实例。

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString：：附加

将指定的`HString`对象与当前`HString`对象关联。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>参数

*赫斯特*<br/>
一个现有的 `HString` 对象。

## <a name="hstringcopyto"></a><a name="copyto"></a>HString：：复制到

将当前`HString`对象复制到 HSTRING 对象。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*Str*<br/>
接收副本的 HSTRING。

### <a name="remarks"></a>备注

此方法调用[Windows 复制字符串](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)函数。

## <a name="hstringdetach"></a><a name="detach"></a>赫斯特林：:D塔奇

取消指定`HString`对象与其基础值的关联。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>返回值

分离操作`HString`开始之前的基础值。

## <a name="hstringget"></a><a name="get"></a>HString：获取

检索基础 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>返回值

基础 HSTRING 句柄的值

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString：获取地址

检索指向基础 HSTRING 句柄的指针。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>返回值

指向基础 HSTRING 句柄的指针。

### <a name="remarks"></a>备注

此操作后，将销毁基础 HSTRING 句柄的字符串值。

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString：：获取原始缓冲区

检索指向基础字符串数据的指针。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>参数

*长度*指向接收数据长度的**int**变量的指针。

### <a name="return-value"></a>返回值

指向基础字符串数据的**const**指针。

## <a name="hstringhstring"></a><a name="hstring"></a>HString：：HString

初始化 `HString` 类的新实例。

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>参数

*赫斯特*<br/>
HSTRING 句柄。

*其他*<br/>
一个现有的 `HString` 对象。

### <a name="remarks"></a>备注

第一个构造函数初始化为空`HString`的新对象。

第二个构造函数将新`HString`对象初始化到现有*其他*参数的值，然后销毁*其他*参数。

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString：：有效

指示当前`HString`对象是否为空。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>参数

如果当前`HString`对象不为空，**则为 true;** 否则，**假**。

## <a name="hstringmakereference"></a><a name="makereference"></a>HString：：使参考

从指定的`HStringReference`字符串参数创建对象。

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

*大小 D 最大*<br/>
指定目标`HStringReference`缓冲区大小的模板参数。

*Str*<br/>
对宽字符串的引用。

*莱恩*<br/>
要在此操作中使用*str*参数缓冲区的最大长度。 如果未指定*len*参数，则使用整个*str*参数。

### <a name="return-value"></a>返回值

其`HStringReference`值与指定的*str*参数相同的对象。

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString：：：运算符= 运算符

将另一`HString`个对象的值移动到当前`HString`对象。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>参数

*其他*<br/>
一个现有的 `HString` 对象。

### <a name="remarks"></a>备注

现有*其他*对象的值将复制到当前`HString`对象，然后销毁*其他*对象。

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString：：：：运算符=运算符

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
要比较的第一个参数。 *lhs*可以是`HString`对象或`HStringReference`对象，也可以是 HSTRING 句柄。

rhs**<br/>
要比较的第二个参数。*rh 可以是*或`HString``HStringReference`对象，也可以是 HSTRING 句柄。

### <a name="return-value"></a>返回值

如果*lhs*和*rhs*参数相等，**则为 true;** 否则，**假**。

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString：：操作员！= 操作员

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
要比较的第一个参数。 *lhs*可以是`HString`对象或`HStringReference`对象，也可以是 HSTRING 句柄。

rhs**<br/>
要比较的第二个参数。*rh 可以是*或`HString``HStringReference`对象，也可以是 HSTRING 句柄。

### <a name="return-value"></a>返回值

如果*lhs*和*rhs*参数不相等，**则为 true;** 否则，**假**。

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString：：操作员&lt;

指示第一个参数是否小于第二个参数。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是 对 的`HString`引用。

rhs**<br/>
要比较的第二个参数。 *rhs*可以是对 的`HString`引用。

### <a name="return-value"></a>返回值

如果*lhs*参数小于*rhs*参数，**则为 true;** 否则，**假**。

## <a name="hstringrelease"></a><a name="release"></a>HString：：发布

删除基础字符串值并将当前`HString`对象归为空值。

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString：：设置

将当前`HString`对象的值设置到指定的宽字符字符串或`HString`参数。

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

*Str*<br/>
宽字符字符串。

*莱恩*<br/>
分配给当前`HString`对象的*str*参数的最大长度。

*赫斯特*<br/>
一个现有的 `HString` 对象。
