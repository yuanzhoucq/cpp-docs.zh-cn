---
title: ctype_byname 类
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: dcaaff45fb33155710f788af4ceb657eff97464e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689737"
---
# <a name="ctype_byname-class"></a>ctype_byname 类

派生类模板描述了一个对象，该对象可充当给定区域设置的 ctype facet，启用字符分类以及区分大小写和本地和区域设置指定字符集之间的字符的转换。

## <a name="syntax"></a>语法

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>备注

其行为由已命名的区域设置 `_Locname` 决定。 每个构造函数对具有 [ctype](../standard-library/ctype-class.md)\<CharType 1> ( `_Refs`) 的基对象或基类 `ctype<char>` 的同等对象进行初始化。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
