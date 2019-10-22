---
title: codecvt_byname 类
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: b48f01126eba7082230fc5e19150d42d1dfad2f3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688291"
---
# <a name="codecvt_byname-class"></a>codecvt_byname 类

一个派生类模板，用于描述一个对象，该对象可充当给定区域设置的排序规则 facet，从而能够检索涉及转换的文化区域的信息。

## <a name="syntax"></a>语法

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>参数

*_Locname* \
已命名的区域设置。

*_Refs* \
初始引用计数。

## <a name="remarks"></a>备注

构造已命名的区域设置时，将自动创建 Byname facet。

其行为由已命名的区域设置 *_Locname*确定。 每个构造函数使用 [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte, StateType>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
