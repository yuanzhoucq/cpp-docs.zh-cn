---
title: HStringReference 类
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
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
ms.openlocfilehash: b9d2e49d0a7e1321e2259c06e1313a90d55dc90e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784092"
---
# <a name="hstringreference-class"></a>HStringReference 类

表示从现有字符串创建的 HSTRING。

## <a name="syntax"></a>语法

```cpp
class HStringReference;
```

## <a name="remarks"></a>备注

在新 HSTRING 的后备缓冲区的生存期不受 Windows 运行时。 调用方分配堆栈帧，以避免堆分配并消除内存泄漏的风险上的源字符串。 此外，调用方必须确保源字符串在附加 HSTRING 的生存期内保持不变。 有关详细信息，请参阅[WindowsCreateStringReference 函数](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                    | 描述
------------------------------------------------------- | -----------------------------------------------------------
[Hstringreference:: Hstringreference](#hstringreference) | 初始化 `HStringReference` 类的新实例。

### <a name="public-methods"></a>公共方法

成员                              | 描述
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 复制当前`HStringReference`到 HSTRING 对象的对象。
[HStringReference::Get](#get)       | 检索基础 HSTRING 句柄的值。

### <a name="public-operators"></a>公共运算符

名称                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | 另一个的值移`HStringReference`对象与当前`HStringReference`对象。
[HStringReference::operator==](#operator-equality)    | 指示两个参数是否相等。
[HStringReference::operator!=](#operator-inequality)  | 指示两个参数是否不相等。
[HStringReference::operator&lt;](#operator-less-than) | 指示第一个参数是否小于第二个参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HStringReference`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="copyto"></a>HStringReference::CopyTo

复制当前`HStringReference`到 HSTRING 对象的对象。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*str*<br/>
接收副本的 HSTRING。

### <a name="remarks"></a>备注

此方法调用[WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring)函数。

## <a name="get"></a>HStringReference::Get

检索基础 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>返回值

基础 HSTRING 句柄的值。

## <a name="hstringreference"></a>Hstringreference:: Hstringreference

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
一个模板参数，指定的目标大小`HStringReference`缓冲区。

*str*<br/>
对宽字符串的引用。

len<br/>
最大长度*str*要在此操作中使用的参数缓冲区。 如果*len*参数未指定，整个*str*使用参数。 如果*len*大于*sizeDest*， *len*设置为*sizeDest*-1。

*other*<br/>
另一个`HStringReference`对象。

### <a name="remarks"></a>备注

第一个构造函数初始化新`HStringReference`对象相同大小与参数*str*。

第二个构造函数初始化新`HStringReference`对象由参数大小指定*len*。

第三个构造函数初始化新`HStringReference`的值的对象*其他*参数，然后再销毁*其他*参数。

## <a name="operator-assign"></a>HStringReference::operator=

另一个的值移`HStringReference`对象与当前`HStringReference`对象。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>参数

*other*<br/>
一个现有的 `HStringReference` 对象。

### <a name="remarks"></a>备注

现有值*其他*对象复制到当前`HStringReference`对象，然后*其他*对象被销毁。

## <a name="operator-equality"></a>Hstringreference:: Operator = =

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
要比较的第一个参数。 *lhs*可以是`HStringReference`对象或 HSTRING 句柄。

*rhs*<br/>
要比较的第二个参数。  *rhs*可以是`HStringReference`对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

**true**如果*lhs*并*rhs*参数不相等; 否则为**false**。

## <a name="operator-inequality"></a>Hstringreference:: Operator ！ =

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
要比较的第一个参数。 *lhs*可以是`HStringReference`对象或 HSTRING 句柄。

*rhs*<br/>
要比较的第二个参数。  *rhs*可以是`HStringReference`对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

**true**如果*lhs*并*rhs*参数是否不相等; 否则为**false**。

## <a name="operator-less-than"></a>HStringReference::operator&lt;

指示第一个参数是否小于第二个参数。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是对引用`HStringReference`。

*rhs*<br/>
要比较的第二个参数。  *rhs*可以是对引用`HStringReference`。

### <a name="return-value"></a>返回值

**true**如果*lhs*参数是小于*rhs*参数; 否则为**false**。
