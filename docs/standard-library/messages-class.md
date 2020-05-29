---
title: messages 类
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: deb9eaedba3c99bb2fcb8399ac412ccedb11545f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375913"
---
# <a name="messages-class"></a>messages 类

类模板描述一个对象，该对象可用作区域设置，用于从给定区域设置的国际化消息目录中检索本地化的消息。

目前，虽然已实现消息类，但没有任何消息。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>参数

*字符类型*\
在程序中用于对区域设置中的字符进行编码的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

大致来说，此 facet 会打开基类 messages_base 中定义的消息目录，检索所需要的信息，然后关闭目录。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[消息](#messages)|消息 facet 构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[char_type](#char_type)|一种用于显示消息的字符类型。|
|[string_type](#string_type)|一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[关闭](#close)|关闭消息目录。|
|[do_close](#do_close)|一种为失去消息目录而调用的虚拟函数。|
|[do_get](#do_get)|一种为检索消息目录而调用的虚拟函数。|
|[do_open](#do_open)|一种为打开消息目录而调用的虚拟函数。|
|[get](#get)|检索消息目录。|
|[open](#open)|打开消息目录。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="messageschar_type"></a><a name="char_type"></a>消息：：char_type

一种用于显示消息的字符类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="messagesclose"></a><a name="close"></a>消息：关闭

关闭消息目录。

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>参数

*_Catval*\
要关闭的目录。

### <a name="remarks"></a>备注

此成员函数调用 [do_close](#do_close)(_ *Catval*)。

## <a name="messagesdo_close"></a><a name="do_close"></a>消息：:d_close

一种为失去消息目录而调用的虚拟函数。

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>参数

*_Catval*\
要关闭的目录。

### <a name="remarks"></a>备注

受保护的成员函数关闭消息目录 *_Catval*，该目录必须通过之前对[do_open](#do_open)调用打开。

必须从以前打开的且未关闭的目录获取 *_Catval*。

### <a name="example"></a>示例

请参阅 [close](#close) 的示例，它调用 `do_close`。

## <a name="messagesdo_get"></a><a name="do_get"></a>消息：:do_get

一种为检索消息目录而调用的虚拟函数。

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>参数

*_Catval*\
指定要搜索的消息目录的标识值。

*_Set*\
用于在消息目录中查找消息的第一个标识。

*_Message*\
用于在消息目录中查找消息的第二个标识。

*_Dfault*\
失败时返回的字符串。

### <a name="return-value"></a>返回值

它在发生故障时返回 *_Dfault*的副本。 否则，它返回指定的消息序列的副本。

### <a name="remarks"></a>备注

受保护的成员函数尝试从消息目录 *_Catval*获取消息序列。 在这样做时，它可能会 *_Set*利用 *_Set、_Message*和 *_Dfault。*

### <a name="example"></a>示例

请参阅 [get](#get) 的示例，它调用 `do_get`。

## <a name="messagesdo_open"></a><a name="do_open"></a>消息：:do_打开

一种为打开消息目录而调用的虚拟函数。

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>参数

*_Catname*\
要搜索的目录的名称。

*_Loc*\
目录中要搜索的区域设置。

### <a name="return-value"></a>返回值

失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。

### <a name="remarks"></a>备注

受保护的成员函数尝试打开名称*为_Catname*的消息目录。 在这样做时，它可以利用区域设置 *_Loc*

返回值应用作稍后对 [close](#close) 调用时的自变量。

### <a name="example"></a>示例

请参阅 [open](#open) 的示例，它调用 `do_open`。

## <a name="messagesget"></a><a name="get"></a>消息：获取

检索消息目录。

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>参数

*_Catval*\
指定要搜索的消息目录的标识值。

*_Set*\
用于在消息目录中查找消息的第一个标识。

*_Message*\
用于在消息目录中查找消息的第二个标识。

*_Dfault*\
失败时返回的字符串。

### <a name="return-value"></a>返回值

它在发生故障时返回 *_Dfault*的副本。 否则，它返回指定的消息序列的副本。

### <a name="remarks"></a>备注

成员函数返回[do_get](#do_get) `_Catval`（、 `_Set` `_Message`、 `_Dfault`。 。 。 。 。

## <a name="messagesmessages"></a><a name="messages"></a>消息：消息

消息 facet 构造函数。

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*\
用于指定对象的内存管理类型的整数值。

*_Locname*\
区域设置的名称。

### <a name="remarks"></a>备注

*_Refs*参数的可能值及其显著性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \>1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数用区域设置初始化其基本对象 **：：**[分面](../standard-library/locale-class.md#facet_class)（ `_Refs`。

## <a name="messagesopen"></a><a name="open"></a>消息：：打开

打开消息目录。

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>参数

*_Catname*\
要搜索的目录的名称。

*_Loc*\
目录中要搜索的区域设置。

### <a name="return-value"></a>返回值

失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。

### <a name="remarks"></a>备注

成员函数返回[do_open](#do_open) `_Catname`（。 `_Loc`

## <a name="messagesstring_type"></a><a name="string_type"></a>消息：：string_type

一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[basic_string](../standard-library/basic-string-class.md)其对象可以存储消息序列的副本。

## <a name="see-also"></a>另请参阅

[\<区域设置>](../standard-library/locale.md)\
[messages_base类](../standard-library/messages-base-class.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
