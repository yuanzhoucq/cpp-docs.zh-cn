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
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371426"
---
# <a name="hstringreference-class"></a>HStringReference 类

表示从现有字符串创建的 HSTRING。

## <a name="syntax"></a>语法

```cpp
class HStringReference;
```

## <a name="remarks"></a>备注

新 HSTRING 中备份缓冲区的生存期不由 Windows 运行时管理。 调用方在堆栈帧上分配源字符串，以避免堆分配并消除内存泄漏的风险。 此外，调用方必须确保源字符串在附加 HSTRING 的生存期内保持不变。 有关详细信息，请参阅[Windows 创建String参照函数](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                    | 说明
------------------------------------------------------- | -----------------------------------------------------------
[HString 参考：：HString 参考](#hstringreference) | 初始化 `HStringReference` 类的新实例。

### <a name="public-methods"></a>公共方法

成员                              | 说明
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 将当前`HStringReference`对象复制到 HSTRING 对象。
[HString 参考：获取](#get)       | 检索基础 HSTRING 句柄的值。
[HString 参考：：获取原始缓冲区](#getrawbuffer) | 检索指向基础字符串数据的指针。

### <a name="public-operators"></a>公共运算符

名称                                                  | 说明
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HString 参考：：运算符*](#operator-assign)       | 将另一`HStringReference`个对象的值移动到当前`HStringReference`对象。
[HString 参考：：运算符 *](#operator-equality)    | 指示两个参数是否相等。
[HString 参考：：操作员！](#operator-inequality)  | 指示两个参数是否不相等。
[HString 参考：：运算符&lt;](#operator-less-than) | 指示第一个参数是否小于第二个参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HStringReference`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HString 参考：：复制到

将当前`HStringReference`对象复制到 HSTRING 对象。

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

## <a name="hstringreferenceget"></a><a name="get"></a>HString 参考：获取

检索基础 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>返回值

基础 HSTRING 句柄的值。

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HString 参考：：获取原始缓冲区

检索指向基础字符串数据的指针。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>参数

*长度*指向接收数据长度的**int**变量的指针。

### <a name="return-value"></a>返回值

指向基础字符串数据的**const**指针。

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HString 参考：：HString 参考

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

*大小 D 最大*<br/>
指定目标`HStringReference`缓冲区大小的模板参数。

*Str*<br/>
对宽字符串的引用。

*莱恩*<br/>
要在此操作中使用*str*参数缓冲区的最大长度。 如果未指定*len*参数，则使用整个*str*参数。 如果*len*大于*大小 D，**则 len*设置为大小 D*最大*-1。

*其他*<br/>
另`HStringReference`一个对象。

### <a name="remarks"></a>备注

第一个构造函数初始化了与`HStringReference`参数*str*大小相同的新对象。

第二个构造函数初始化了大小`HStringReference`按参数*len*指定的新对象。

第三个构造函数将新`HStringReference`对象初始化到*其他*参数的值，然后销毁*另一个*参数。

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HString 参考：：运算符*

将另一`HStringReference`个对象的值移动到当前`HStringReference`对象。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>参数

*其他*<br/>
一个现有的 `HStringReference` 对象。

### <a name="remarks"></a>备注

现有*其他*对象的值将复制到当前`HStringReference`对象，然后销毁*其他*对象。

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HString 参考：：运算符 *

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

rhs**<br/>
要比较的第二个参数。  *rhs*可以是`HStringReference`对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

如果*lhs*和*rhs*参数相等，**则为 true;** 否则，**假**。

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HString 参考：：操作员！

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

rhs**<br/>
要比较的第二个参数。  *rhs*可以是`HStringReference`对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

如果*lhs*和*rhs*参数不相等，**则为 true;** 否则，**假**。

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HString 参考：：运算符&lt;

指示第一个参数是否小于第二个参数。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是 对 的`HStringReference`引用。

rhs**<br/>
要比较的第二个参数。  *rhs*可以是对 的`HStringReference`引用。

### <a name="return-value"></a>返回值

如果*lhs*参数小于*rhs*参数，**则为 true;** 否则，**假**。
