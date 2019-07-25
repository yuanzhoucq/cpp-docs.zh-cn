---
title: messages_byname 类
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: b8fe1ab2db792819831f5c50aa99a02559f71cdd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451808"
---
# <a name="messagesbyname-class"></a>messages_byname 类

该派生模板类描述一个可充当给定区域设置的信息 facet 的对象，从而检索本地化消息。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>参数

*_Locname*\
已命名的区域设置。

*_Refs*\
初始引用计数。

## <a name="remarks"></a>备注

其行为由已命名的区域设置 *_Locname*确定。 每个构造函数通过 [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
