---
title: ctype&lt;char&gt; 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
dev_langs:
- C++
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faed3af6595b37146bfd565e09e9ceeea3ca5d73
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217649"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; 类

此类是模板类的显式专用化`ctype\<CharType>`键入**char**，描述一个对象来充当区域设置 facet 以各种类型的字符属性特征化**char**.

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

显式专用化与模板类存在以下几个方面的差异：

- Ctype 类的对象 < `char`> 将存储到 ctype 掩码表的第一个元素，数组的 UCHAR_MAX + 1 个元素的类型的指针`ctype_base::mask`。 它还存储布尔对象，指明当 ctype\< **Elem**> 对象被销毁时是否应（使用 `operator delete[]`）删除数组。

- 其唯一的公共构造函数允许您指定`tab`，ctype 掩码表，并`del`，如果应为数组，则为 true 的布尔对象时删除 ctype < `char`> 对象被销毁后，引用计数以及参数引用。

- 受保护的成员函数`table`返回存储的 ctype 掩码表。

- 静态成员对象`table_size`ctype 掩码表中指定元素的最小数目。

- 受保护的静态成员函数`classic_table`（返回适合于"C"区域设置的 ctype 掩码表。

- 没有受保护的虚拟成员函数 [do_is](../standard-library/ctype-class.md#do_is)、[do_scan_is](../standard-library/ctype-class.md#do_scan_is)，或 [do_scan_not](../standard-library/ctype-class.md#do_scan_not)。 相应的公共成员函数自身执行等效操作。

成员函数 [do_narrow](../standard-library/ctype-class.md#do_narrow) 和 [do_widen](../standard-library/ctype-class.md#do_widen) 复制未改变的元素。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[facet 类](locale-class.md#facet_class)<br/>
[ctype_base 类](../standard-library/ctype-base-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
