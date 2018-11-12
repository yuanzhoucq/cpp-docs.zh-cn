---
title: 地址存储
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 2a0e218d4d34fa1482986ecccd7da8adba38086b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539368"
---
# <a name="storage-of-addresses"></a>地址存储

地址所需的存储量和该地址的含义取决于编译器的实现。 指向不同类型的指针不能保证具有相同的长度。 因此，sizeof(char \*) 不必与 sizeof(int \*) 相等。

**Microsoft 专用**

对于 Microsoft C 编译器，sizeof(char \*) 与 sizeof(int \*) 相等。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[指针声明](../c-language/pointer-declarations.md)