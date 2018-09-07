---
title: messages_byname 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmes/std::messages_byname
dev_langs:
- C++
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e03cb627e7e9db40d56a69112977d87141626696
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100439"
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

*_Locname*<br/>
已命名的区域设置。

*_Refs*<br/>
初始引用计数。

## <a name="remarks"></a>备注

其行为由命名的区域设置确定 *_Locname*。 每个构造函数通过 [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
