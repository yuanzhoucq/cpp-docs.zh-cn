---
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: ed780e059a5e456731fd6a4f651639e282016f5e
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341100"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

包括 C 标准库标头\<stdbool > 并将关联名称添加`std`到命名空间。

> [!NOTE]
> 由于 stdbool > 标头定义了作为关键字的宏C++, 其中包括不起作用。 \< 中\< C++弃用了 stdbool > 标头。 \<Cstdbool > 标头在 c + + 17 中已弃用, 并已在草案 c + + 20 标准中删除。

## <a name="requirements"></a>要求

**标头:** \<cstdbool >

**命名空间：** std

## <a name="remarks"></a>备注

包括此标头可确保在`std`命名空间中声明使用 C 标准库标头中的外部链接声明的名称。

## <a name="see-also"></a>请参阅

[标头文件引用](cpp-standard-library-header-files.md)\
[C++标准库概述](cpp-standard-library-overview.md)\
[标准库中的C++线程安全](thread-safety-in-the-cpp-standard-library.md)
