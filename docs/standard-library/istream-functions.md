---
title: '&lt;istream&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363069"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 函数

|||
|-|-|
|[交换](#istream_swap)|[Ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>交换

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

*离开*\
一个流。

*对*\
一个流。

## <a name="ws"></a><a name="ws"></a>Ws

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

操纵器提取`ch`并丢弃[use_facet](../standard-library/basic-filebuf-class.md#open)< **型**\<**Elem> >（getloc）** 的任何元素。 [getloc](../standard-library/ios-base-class.md#getloc) **is**( **ctype**\< **Elem**>:: **space**, **ch**) 为 true。

此函数如果在提取元素时遇到文件末尾，则会调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**)。 它返回 *_Istr*。

### <a name="example"></a>示例

有关使用 `ws` 的示例，请参阅 [operator>>](../standard-library/istream-operators.md#op_gt_gt)。

## <a name="see-also"></a>另请参阅

[\<istream>](../standard-library/istream.md)
