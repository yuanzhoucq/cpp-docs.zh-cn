---
title: codecvt_base 类
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6fca9b2130407b165a7a7bfb1fb2a9ec81774e20
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689890"
---
# <a name="codecvt_base-class"></a>codecvt_base 类

用于定义称为 `result` 的枚举类型的 codecvt 类的基类，此类枚举类型用作 facet 成员函数的返回类型，以指示转换的结果。

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

类描述类模板[codecvt](../standard-library/codecvt-class.md)的所有专用化所共有的枚举。 枚举结果描述了来自 [do_in](../standard-library/codecvt-class.md#do_in) 或 [do_out](../standard-library/codecvt-class.md#do_out) 可能的返回值：

- `ok` 内部和外部字符编码之间的转换是否成功。

- `partial` 如果目标不够大，则无法成功转换。

- 如果源序列的格式不正确，则 `error`。

- 如果函数不执行任何转换，则为 `noconv`。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
