---
title: time_put_byname 类
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: 2da2bf4ea1c709b820c1a82dc20e288634139a83
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459995"
---
# <a name="timeputbyname-class"></a>time_put_byname 类

一种派生模板类，用于描述一个可充当类型 `time_put`\< CharType, OutputIterator > 的区域设置 facet 的对象。

## <a name="syntax"></a>语法

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>参数

*_Locname*\
区域设置名称。

*_Refs*\
初始引用计数。

## <a name="remarks"></a>备注

其行为由已[命名](../standard-library/locale-class.md#name)的区域设置 *_Locname*确定。 每个构造函数通过[time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > (`_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
