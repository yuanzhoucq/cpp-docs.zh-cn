---
title: '&lt;ccomplex&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ccomplex>
- ccomplex
helpviewer_keywords:
- ccomplex header
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: 5b5383b1eca4fda72f5f9e3a78637373acbcf7ab
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341137"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

包括C++标准库标头[ \<复杂 >](complex.md)。

> [!NOTE]
> \<Ccomplex > 不包含\<C 标准库 complex .h > 标头, 因为它实际上被复杂 > 和\<h > C++中\<的重载替换。 这会使\<ccomplex > 标头冗余。 不推荐使用C++复杂的.h>标\<头。 \<Ccomplex > 标头在 c + + 17 中已弃用, 并已在草案 c + + 20 标准中删除。

## <a name="requirements"></a>要求

**标头:** \<ccomplex >

**命名空间：** std

## <a name="remarks"></a>备注

在 iostream `clog`中声明的名称 ( \<在复杂的 .h > 中声明`std` ) 未在命名空间中定义, 因为`clog`可能与在[ \<>](iostream.md)中声明的发生冲突。

## <a name="see-also"></a>请参阅

[\<复杂 >](complex.md)\
[\<cmath 1>](cmath.md)\
[标头文件引用](cpp-standard-library-header-files.md)\
[C++标准库概述](cpp-standard-library-overview.md)\
[标准库中的C++线程安全](thread-safety-in-the-cpp-standard-library.md)
