---
title: "&lt;ostream&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ostream/std::operator&lt;&lt;
dev_langs:
- C++
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34691953d5d0482b291f7c9cfba9f5f28fb27ddd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; 运算符
||  
|-|  
|[operator&lt;&lt;](#op_lt_lt)|  
  
##  <a name="op_lt_lt"></a>  operator&lt;&lt;  
 将各种类型写入流。  
  
```
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```  
  
### <a name="parameters"></a>参数  
 `_Ch`  
 一个字符。  
  
 `_Elem`  
 元素类型。  
  
 `_Ostr`  
 一个 `basic_ostream` 对象。  
  
 `str`  
 字符串。  
  
 `_Tr`  
 字符特征。  
  
 `val`  
 类型  
  
### <a name="return-value"></a>返回值  
 流。  
  
### <a name="remarks"></a>备注  
 `basic_ostream` 类还定义了多个插入运算符。 有关详细信息，请参阅 [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt)。  
  
 模板函数  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```  
  
 确定以 `str` 开始的序列的长度 N = `traits_type::`[length](../standard-library/char-traits-struct.md#length)( `str`)，并插入序列。 如果 N < `_Ostr.`[width](../standard-library/ios-base-class.md#width)，则该函数还将插入 `_Ostr.width` 的重复项 - N 个填充字符。 重复项在序列前，前提是 ( `_Ostr`. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left)。 否则，重复项在该序列后。 该函数返回 `_Ostr`。  
  
 模板函数  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 插入元素 `_Ch`。 如果 1 < `_Ostr.width`，则该函数还将插入 `_Ostr.width` 的重复项 - 1 个填充字符。 如果 `_Ostr.flags & adjustfield != left`，则该重复项在序列前。 否则，重复项在该序列后。 它将返回 `_Ostr`。  
  
 模板函数  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```  
  
 行为等同于  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```  
  
 通过调用 `_Ostr.`[put](../standard-library/basic-ostream-class.md#put)( `_Ostr.`[widen](../standard-library/basic-ios-class.md#widen)( `_Ch`)) 将以 `str` 开头的序列的每个元素 `_Ch` 转换为 `Elem` 类型的对象除外。  
  
 模板函数  
  
```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```  
  
 行为等同于  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 通过调用 `_Ostr.put`( `_Ostr.widen`( `_Ch`)) 将 `_Ch` 转换为 `Elem` 类型的对象除外。  
  
 模板函数  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```  
  
 行为等同于  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```  
  
 （在插入元素之前，无需将其加宽。）  
  
 模板函数  
  
```cpp  
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```  
  
 行为等同于  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 （在插入 `_Ch` 之前，无需将其加宽。）  
  
 模板函数  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```  
  
 返回 `_Ostr` << ( `const char *`) `str`。  
  
 模板函数  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```  
  
 返回 `_Ostr` << ( `char`) `_Ch`。  
  
 模板函数：  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```  
  
 返回 `_Ostr` << ( `const char *`) `str`。  
  
 模板函数：  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```  
  
 返回 `_Ostr` << ( `char`) `_Ch`。  
  
 模板函数：  
  
```cpp  
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```  
  
 返回 `_Ostr` `<<` `val`（并将[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)转换为进程中左值的 `_Ostr`）。  
  
### <a name="example"></a>示例  
  有关使用 `operator<<` 的示例，请参阅 [flush](../standard-library/ostream-functions.md#flush)。  
  
## <a name="see-also"></a>请参阅  
 [\<ostream>](../standard-library/ostream.md)



