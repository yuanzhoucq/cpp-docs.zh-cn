---
title: "messages 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- messages
- xlocmes/std::messages
- locale/std::messages::char_type
- locale/std::messages::string_type
- locale/std::messages::close
- locale/std::messages::do_close
- locale/std::messages::do_get
- locale/std::messages::do_open
- locale/std::messages::get
- locale/std::messages::open
dev_langs:
- C++
helpviewer_keywords:
- messages class
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 8a3c647c9c64f2783bf2bc6d2eee86d7107af8d2
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="messages-class"></a>messages 类
此模板类描述一个对象来充当区域设置 facet，以便从给定区域设置的国际化消息目录中检索本地化消息。  
  
 目前，虽然已实现消息类，但没有任何消息。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType>  
class messages : public messages_base;
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。  
  
 大致来说，此 facet 会打开基类 messages_base 中定义的消息目录，检索所需要的信息，然后关闭目录。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[messages](#messages)|消息 facet 构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#char_type)|一种用于显示消息的字符类型。|  
|[string_type](#string_type)|一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[close](#close)|关闭消息目录。|  
|[do_close](#do_close)|一种为失去消息目录而调用的虚拟函数。|  
|[do_get](#do_get)|一种为检索消息目录而调用的虚拟函数。|  
|[do_open](#do_open)|一种为打开消息目录而调用的虚拟函数。|  
|[get](#get)|检索消息目录。|  
|[open](#open)|打开消息目录。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
##  <a name="char_type"></a>messages::char_type  
 一种用于显示消息的字符类型。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **CharType** 的同义词。  
  
##  <a name="close"></a>messages::close  
 关闭消息目录。  
  
```
void close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>参数  
 `_Catval`  
 要关闭的目录。  
  
### <a name="remarks"></a>备注  
 此成员函数调用 [do_close](#do_close)(_ *Catval*)。  
  
##  <a name="do_close"></a>messages::do_close  
 一种为失去消息目录而调用的虚拟函数。  
  
```
virtual void do_close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>参数  
 `_Catval`  
 要关闭的目录。  
  
### <a name="remarks"></a>备注  
 受保护的成员函数将关闭消息目录 `_Catval`，该目录必须已通过对 [do_open](#do_open) 的早期调用处于打开状态。  
  
 必须从以前打开的且未关闭的目录获取 *_Catval*。  
  
### <a name="example"></a>示例  
  请参阅 [close](#close) 的示例，它调用 `do_close`。  
  
##  <a name="do_get"></a>messages::do_get  
 一种为检索消息目录而调用的虚拟函数。  
  
```
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>参数  
 `_Catval`  
 指定要搜索的消息目录的标识值。  
  
 `_Set`  
 用于在消息目录中查找消息的第一个标识。  
  
 `_Message`  
 用于在消息目录中查找消息的第二个标识。  
  
 `_Dfault`  
 失败时返回的字符串。  
  
### <a name="return-value"></a>返回值  
 它在失败时返回 `_Dfault` 的副本。 否则，它返回指定的消息序列的副本。  
  
### <a name="remarks"></a>备注  
 受保护的成员函数会尝试从消息目录 `_Catval` 中获取消息序列。 执行此操作时，它可能会使用 `_Set`、`_Message` 和 `_Dfault`。  
  
### <a name="example"></a>示例  
  请参阅 [get](#get) 的示例，它调用 `do_get`。  
  
##  <a name="do_open"></a>messages::do_open  
 一种为打开消息目录而调用的虚拟函数。  
  
```
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>参数  
 `_Catname`  
 要搜索的目录的名称。  
  
 `_Loc`  
 目录中要搜索的区域设置。  
  
### <a name="return-value"></a>返回值  
 失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。  
  
### <a name="remarks"></a>备注  
 受保护的成员函数会尝试打开名称为 `_Catname` 的消息目录。 执行此操作时，它可能会使用区域设置 `_Loc`  
  
 返回值应用作稍后对 [close](#close) 调用时的自变量。  
  
### <a name="example"></a>示例  
  请参阅 [open](#open) 的示例，它调用 `do_open`。  
  
##  <a name="get"></a>messages::get  
 检索消息目录。  
  
```
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>参数  
 `_Catval`  
 指定要搜索的消息目录的标识值。  
  
 `_Set`  
 用于在消息目录中查找消息的第一个标识。  
  
 `_Message`  
 用于在消息目录中查找消息的第二个标识。  
  
 `_Dfault`  
 失败时返回的字符串。  
  
### <a name="return-value"></a>返回值  
 它在失败时返回 `_Dfault` 的副本。 否则，它返回指定的消息序列的副本。  
  
### <a name="remarks"></a>备注  
 成员函数返回 [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`)。  
  
##  <a name="messages"></a>messages::messages  
 消息 facet 构造函数。  
  
```
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```  
  
### <a name="parameters"></a>参数  
 `_Refs`  
 用于指定对象的内存管理类型的整数值。  
  
 `_Locname`  
 区域设置的名称。  
  
### <a name="remarks"></a>备注  
 `_Refs` 参数可能的值及其含义：  
  
-   0：对象的生存期由包含该对象的区域设置管理。  
  
-   1：必须手动管理对象的生存期。  
  
-   \>1︰ 未定义这些值。  
  
 由于该析构函数受到保护，可能没有直接的示例。  
  
 构造函数通过 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 初始化其基对象。  
  
##  <a name="open"></a>messages::open  
 打开消息目录。  
  
```
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>参数  
 `_Catname`  
 要搜索的目录的名称。  
  
 `_Loc`  
 目录中要搜索的区域设置。  
  
### <a name="return-value"></a>返回值  
 失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。  
  
### <a name="remarks"></a>备注  
 成员函数返回 [do_open](#do_open)( `_Catname`, `_Loc`)。  
  
##  <a name="string_type"></a>messages::string_type  
 一种类型，此类型描述包含 **CharType** 类型字符的 `basic_string` 类型字符串。  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>备注  
 此类型描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化，该模板类的对象可存储消息序列的副本。  
  
## <a name="see-also"></a>另请参阅  
 [\<locale>](../standard-library/locale.md)   
 [messages_base 类](../standard-library/messages-base-class.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




