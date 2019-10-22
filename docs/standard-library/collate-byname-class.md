---
title: collate_byname 类
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688274"
---
# <a name="collate_byname-class"></a>collate_byname 类

一个派生类模板，用于描述一个对象，该对象可充当给定区域设置的排序规则 facet，从而能够检索特定于涉及字符串排序约定的区域性区域的信息。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>参数

*_Locname* \
已命名的区域设置。

*_Refs* \
初始引用计数。

## <a name="remarks"></a>备注

类模板描述了一个对象，该对象可充当类型为[collate](../standard-library/collate-class.md#collate) \<CharType > 的[区域设置 facet](../standard-library/locale-class.md#facet_class) 。 其行为由已[命名](../standard-library/locale-class.md#name)的区域设置 *_Locname*确定。 每个构造函数通过 [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
