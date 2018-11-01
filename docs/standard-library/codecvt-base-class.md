---
title: codecvt_base 类
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6f957c39f9c78fd182b7ba2a14bdab7f27db56ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520622"
---
# <a name="codecvtbase-class"></a>codecvt_base 类

用于定义枚举类型的 codecvt 类的基类称为`result`、 用作 facet 成员函数的返回类型以便指示转换的结果。

## <a name="syntax"></a>语法

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>备注

此类会描述常用于所有模板类 [codecvt](../standard-library/codecvt-class.md) 专用化的枚举。 枚举结果描述了来自 [do_in](../standard-library/codecvt-class.md#do_in) 或 [do_out](../standard-library/codecvt-class.md#do_out) 可能的返回值：

- `ok` 如果内部和外部字符编码之间的转换会成功。

- `partial` 如果目标是不足够大，以便使转换成功完成。

- `error` 如果源序列格式不，正确。

- 如果函数不执行任何转换，则为 `noconv`。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
