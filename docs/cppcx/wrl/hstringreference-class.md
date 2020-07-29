---
title: HStringReference 类
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: 871696f4a970b1ef9d1f5d36d2e17184b93c9e8b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212977"
---
# <a name="hstringreference-class"></a>HStringReference 类

表示从现有字符串创建的 HSTRING。

## <a name="syntax"></a>语法

```cpp
class HStringReference;
```

## <a name="remarks"></a>备注

新 HSTRING 中的后备缓冲区的生存期不受 Windows 运行时管理。 调用方在堆栈帧上分配一个源字符串，以避免堆分配并消除内存泄漏的风险。 此外，调用方必须确保源字符串在附加的 HSTRING 的生存期内保持不变。 有关详细信息，请参阅[WindowsCreateStringReference 函数](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

“属性”                                                    | 描述
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference：： HStringReference](#hstringreference) | 初始化 `HStringReference` 类的新实例。

### <a name="public-methods"></a>公共方法

成员                              | 描述
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 将当前 `HStringReference` 对象复制到 HSTRING 对象。
[HStringReference：： Get](#get)       | 检索基础 HSTRING 句柄的值。
[HStringReference：： GetRawBuffer](#getrawbuffer) | 检索指向基础字符串数据的指针。

### <a name="public-operators"></a>公共运算符

名称                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference：： operator =](#operator-assign)       | 将另一个对象的值移动 `HStringReference` 到当前 `HStringReference` 对象。
[HStringReference：： operator = =](#operator-equality)    | 指示两个参数是否相等。
[HStringReference：： operator！ =](#operator-inequality)  | 指示两个参数是否不相等。
[HStringReference：： operator&lt;](#operator-less-than) | 指示第一个参数是否小于第二个参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HStringReference`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference：： CopyTo

将当前 `HStringReference` 对象复制到 HSTRING 对象。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*字符串*<br/>
接收副本的 HSTRING。

### <a name="remarks"></a>备注

此方法调用[WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)函数。

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference：： Get

检索基础 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>返回值

基础 HSTRING 句柄的值。

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference：： GetRawBuffer

检索指向基础字符串数据的指针。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>参数

*长度*指向一个 **`int`** 变量的指针，该变量接收数据的长度。

### <a name="return-value"></a>返回值

**`const`** 指向基础字符串数据的指针。

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference：： HStringReference

初始化 `HStringReference` 类的新实例。

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>参数

*sizeDest*<br/>
一个模板参数，指定目标缓冲区的大小 `HStringReference` 。

*字符串*<br/>
对宽字符串的引用。

*长度*<br/>
要在此操作中使用的*str*参数缓冲区的最大长度。 如果未指定*len*参数，则使用整个*str*参数。 如果*len*大于*sizeDest*，则*len*设置为*sizeDest*-1。

*以外*<br/>
另一个 `HStringReference` 对象。

### <a name="remarks"></a>备注

第一个构造函数初始化一个与 `HStringReference` 参数*str*大小相同的新对象。

第二个构造函数 `HStringReference` 将初始化大小由参数*长度*的新对象。

第三个构造函数将新的 `HStringReference` 对象初始化为*其他*参数的值，然后销毁*其他*参数。

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference：： operator =

将另一个对象的值移动 `HStringReference` 到当前 `HStringReference` 对象。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>参数

*以外*<br/>
一个现有的 `HStringReference` 对象。

### <a name="remarks"></a>备注

现有的*其他*对象的值将复制到当前 `HStringReference` 对象，然后*其他*对象将被销毁。

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference：： operator = =

指示两个参数是否相等。

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是 `HStringReference` 对象或 HSTRING 句柄。

rhs**<br/>
要比较的第二个参数。  *rhs*可以是 `HStringReference` 对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

**`true`** 如果*lhs*和*rhs*参数相等，则为;否则为 **`false`** 。

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference：： operator！ =

指示两个参数是否不相等。

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是 `HStringReference` 对象或 HSTRING 句柄。

rhs**<br/>
要比较的第二个参数。  *rhs*可以是 `HStringReference` 对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

**`true`** 如果*lhs*和*rhs*参数不相等，则为; 否则为。否则为 **`false`** 。

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference：： operator&lt;

指示第一个参数是否小于第二个参数。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是对的引用 `HStringReference` 。

rhs**<br/>
要比较的第二个参数。  *rhs*可以是对的引用 `HStringReference` 。

### <a name="return-value"></a>返回值

**`true`** 如果*lhs*参数小于*rhs*参数，则为; 否则为。否则为 **`false`** 。
