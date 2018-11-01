---
title: wbuffer_convert 类
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: d19abf74bd9f794bc39ce04e5ed22e360cde75b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476448"
---
# <a name="wbufferconvert-class"></a>wbuffer_convert 类

描述用于控制元素与字节流缓冲区之间的来回传输的流缓冲区。

## <a name="syntax"></a>语法

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*codecvt*|表示转换对象的[区域设置](../standard-library/locale-class.md)方面。|
|*Elem*|宽字符元素类型。|
|*特征*|与 Elem 关联的特征。|

## <a name="remarks"></a>备注

此模板类描述对 `_Elem` 类型的元素（其字符特征由类 `Traits` 描述）与 `std::streambuf` 类型的字节流缓冲区之间的来回传输进行控制的流缓冲区。

一系列 `Elem` 值与多字节序列之间的转换由类 `Codecvt<Elem, char, std::mbstate_t>` 的对象执行，这符合标准代码转换方面 `std::codecvt<Elem, char, std::mbstate_t>` 的要求。

此模板类的对象存储：

- 指向其基础字节流缓冲区的指针

- 指向分配的转换对象（在销毁 [wbuffer_convert](../standard-library/wbuffer-convert-class.md) 对象时释放）的指针
