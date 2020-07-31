---
title: ctype&lt;char&gt; 类
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: d2c74ef46babe388cfa6d649e8b4501b7c235bb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220959"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; 类

类是类模板到类型的显式专用化 `ctype\<CharType>` **`char`** ，它描述可用作区域设置 facet 的对象，以便为类型的字符的各种属性设置特征 **`char`** 。

## <a name="syntax"></a>语法

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>备注

显式专用化的不同之处在于类模板：

- 类的对象 `ctype<char>` 存储一个指向 ctype 掩码表中第一个元素的指针，该指针是一个类型为 UCHAR_MAX + 1 个元素的数组 `ctype_base::mask` 。 它还存储一个布尔对象，该对象指示 `operator delete[]` 在销毁 ctype 对象时是否应删除（使用）数组 \< **Elem**> 。

- 它的唯一公共构造函数允许你指定 `tab` 、ctype 掩码表和 `del` 布尔对象。如果在销毁对象时应删除数组，则为 true `ctype<char>` ; 对于引用计数参数的引用，则为 true。

- 受保护的成员函数 `table` 返回存储的 ctype 掩码表。

- 静态成员对象 `table_size` 指定 ctype 掩码表中元素的最小数目。

- 受保护的静态成员函数 `classic_table` （返回对应于 "C" 区域设置的 ctype 掩码表。

- 没有受保护的虚拟成员函数 [do_is](../standard-library/ctype-class.md#do_is)、[do_scan_is](../standard-library/ctype-class.md#do_scan_is)，或 [do_scan_not](../standard-library/ctype-class.md#do_scan_not)。 相应的公共成员函数自身执行等效操作。

成员函数 [do_narrow](../standard-library/ctype-class.md#do_narrow) 和 [do_widen](../standard-library/ctype-class.md#do_widen) 复制未改变的元素。

## <a name="requirements"></a>要求

**标头：**\<locale>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[facet 类](locale-class.md#facet_class)\
[ctype_base 类](../standard-library/ctype-base-class.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
