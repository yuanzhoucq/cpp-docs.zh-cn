---
title: is_move_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 1b1e450338a123c51b80f40f2369207c8b987cd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383628"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 类

测试类型是否具有移动构造函数。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>参数

*T*<br/>
要计算的类型

## <a name="remarks"></a>备注

类型谓词的计算结果为 true 的类型*T*可以通过使用移动操作构造。 此谓词等效于 `is_constructible<T, T&&>`。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
