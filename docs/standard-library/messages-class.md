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
ms.openlocfilehash: 7a024a8cad8c536b25127d033468874de5ebd8af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568518"
---
# <a name="messages-class"></a>messages 类

此模板类描述一个对象来充当区域设置 facet，以便从给定区域设置的国际化消息目录中检索本地化消息。

目前，虽然已实现消息类，但没有任何消息。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>参数

*CharType*<br/>
在程序中用于对区域设置中的字符进行编码的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

大致来说，此 facet 会打开基类 messages_base 中定义的消息目录，检索所需要的信息，然后关闭目录。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[messages](#messages)|消息 facet 构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种用于显示消息的字符类型。|
|[string_type](#string_type)|一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[close](#close)|关闭消息目录。|
|[do_close](#do_close)|一种为失去消息目录而调用的虚拟函数。|
|[do_get](#do_get)|一种为检索消息目录而调用的虚拟函数。|
|[do_open](#do_open)|一种为打开消息目录而调用的虚拟函数。|
|[get](#get)|检索消息目录。|
|[open](#open)|打开消息目录。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="char_type"></a>messages::char_type

一种用于显示消息的字符类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="close"></a>messages::close

关闭消息目录。

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>参数

*_Catval*<br/>
要关闭的目录。

### <a name="remarks"></a>备注

此成员函数调用 [do_close](#do_close)(_ *Catval*)。

## <a name="do_close"></a>messages::do_close

一种为失去消息目录而调用的虚拟函数。

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>参数

*_Catval*<br/>
要关闭的目录。

### <a name="remarks"></a>备注

受保护的成员函数将关闭消息目录 *_Catval*，其必须具有到的早期调用打开[do_open](#do_open)。

必须从以前打开的且未关闭的目录获取 *_Catval*。

### <a name="example"></a>示例

请参阅 [close](#close) 的示例，它调用 `do_close`。

## <a name="do_get"></a>messages::do_get

一种为检索消息目录而调用的虚拟函数。

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>参数

*_Catval*<br/>
指定要搜索的消息目录的标识值。

*（_s)*<br/>
用于在消息目录中查找消息的第一个标识。

*消息 （_m)*<br/>
用于在消息目录中查找消息的第二个标识。

*_Dfault*<br/>
失败时返回的字符串。

### <a name="return-value"></a>返回值

它将返回一份 *_Dfault*失败。 否则，它返回指定的消息序列的副本。

### <a name="remarks"></a>备注

受保护的成员函数尝试从消息目录中获取消息序列 *_Catval*。 它可能会利用 *_ 设置*，*消息 （_m)*，并 *_Dfault*中执行此操作。

### <a name="example"></a>示例

请参阅 [get](#get) 的示例，它调用 `do_get`。

## <a name="do_open"></a>messages::do_open

一种为打开消息目录而调用的虚拟函数。

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>参数

*_Catname*<br/>
要搜索的目录的名称。

*_Loc*<br/>
目录中要搜索的区域设置。

### <a name="return-value"></a>返回值

失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。

### <a name="remarks"></a>备注

受保护的成员函数尝试打开消息目录的名称是 *_Catname*。 它可能会使用区域设置 *_Loc*中执行此操作

返回值应用作稍后对 [close](#close) 调用时的自变量。

### <a name="example"></a>示例

请参阅 [open](#open) 的示例，它调用 `do_open`。

## <a name="get"></a>messages::get

检索消息目录。

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>参数

*_Catval*<br/>
指定要搜索的消息目录的标识值。

*（_s)*<br/>
用于在消息目录中查找消息的第一个标识。

*消息 （_m)*<br/>
用于在消息目录中查找消息的第二个标识。

*_Dfault*<br/>
失败时返回的字符串。

### <a name="return-value"></a>返回值

它将返回一份 *_Dfault*失败。 否则，它返回指定的消息序列的副本。

### <a name="remarks"></a>备注

成员函数返回 [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`)。

## <a name="messages"></a>messages::messages

消息 facet 构造函数。

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*<br/>
用于指定对象的内存管理类型的整数值。

*_Locname*<br/>
区域设置的名称。

### <a name="remarks"></a>备注

可能的值 *_Refs*参数和其重要性：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数通过 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 初始化其基对象。

## <a name="open"></a>messages::open

打开消息目录。

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>参数

*_Catname*<br/>
要搜索的目录的名称。

*_Loc*<br/>
目录中要搜索的区域设置。

### <a name="return-value"></a>返回值

失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。

### <a name="remarks"></a>备注

成员函数返回 [do_open](#do_open)( `_Catname`, `_Loc`)。

## <a name="string_type"></a>messages::string_type

一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

此类型描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化，该模板类的对象可存储消息序列的副本。

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)<br/>
[messages_base 类](../standard-library/messages-base-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
