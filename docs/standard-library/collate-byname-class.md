---
title: collate_byname 类
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 46eb139bafcf7368688f32cce37e38362c158c91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405178"
---
# <a name="collatebyname-class"></a>collate_byname 类

一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与字符串排序约定有关的文化区域特定信息。

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

*_Locname*<br/>
已命名的区域设置。

*_Refs*<br/>
初始引用计数。

## <a name="remarks"></a>备注

一种模板类，用于描述一个可充当类型 [collate](../standard-library/collate-class.md#collate)\<CharType> 的[区域设置 facet](../standard-library/locale-class.md#facet_class) 的对象。 其行为由[名为](../standard-library/locale-class.md#name)区域设置 *_Locname*。 每个构造函数通过 [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
