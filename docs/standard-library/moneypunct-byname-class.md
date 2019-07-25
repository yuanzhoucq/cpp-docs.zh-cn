---
title: moneypunct_byname 类
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: 47c9d2281973cb57288bfdcf865926fb6dd9ed0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460209"
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname 类

一种派生模板类，用于描述可充当给定区域设置的 `moneypunct` facet 的对象，从而能够格式化货币输入字段或货币输出字段。

## <a name="syntax"></a>语法

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>备注

其行为由已命名的区域设置 `_Locname` 决定。 每个构造函数通过 [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl>( `_Refs`) 初始化其基对象。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
