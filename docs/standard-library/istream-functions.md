---
title: '&lt;istream&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458768"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 函数

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a>  swap

交换两个流对象的元素。

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个流。

*然后*\
一个流。

## <a name="ws"></a>  ws

跳过流中的空白。

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>参数

*_Istr*\
一个流。

### <a name="return-value"></a>返回值

流。

### <a name="remarks"></a>备注

此操控器提取并放弃任何 `ch` 元素，对于这些元素，[use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) 为 true。

此函数如果在提取元素时遇到文件末尾，则会调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**)。 它将返回 *_Istr*。

### <a name="example"></a>示例

有关使用 `ws` 的示例，请参阅 [operator>>](../standard-library/istream-operators.md#op_gt_gt)。

## <a name="see-also"></a>请参阅

[\<istream>](../standard-library/istream.md)
