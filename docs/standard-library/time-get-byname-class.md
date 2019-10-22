---
title: time_get_byname 类
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: 9df3831e085f1dea1df45ff9368479fa516b944e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685756"
---
# <a name="time_get_byname-class"></a>time_get_byname 类

派生类模板描述一个对象，该对象可充当类型 `time_get` \<CharType，InputIterator > 的区域设置 facet。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>参数

*_Locname* \
已命名的区域设置。

*_Refs* \
初始引用计数。

## <a name="requirements"></a>要求

其行为由已命名的区域设置 *_Locname*确定。 每个构造函数都使用 [time_get](../standard-library/time-get-class.md#time_get)\<CharType、InputIterator>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
