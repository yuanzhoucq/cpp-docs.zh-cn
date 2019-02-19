---
title: 地址存储
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148733"
---
# <a name="storage-of-addresses"></a>地址存储

地址所需的存储量和该地址的含义取决于编译器的实现。 指向不同类型的指针不能保证具有相同的长度。 因此，sizeof(char \*) 不必与 sizeof(int \*) 相等。

**Microsoft 专用**

对于 Microsoft C 编译器，sizeof(char \*) 与 sizeof(int \*) 相等。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[指针声明](../c-language/pointer-declarations.md)
