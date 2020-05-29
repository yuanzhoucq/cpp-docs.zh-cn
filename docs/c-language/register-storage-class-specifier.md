---
title: register 存储类说明符
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325242"
---
# <a name="register-storage-class-specifier"></a>register 存储类说明符

**Microsoft 专用**

Microsoft C/C++ 编译器不会按照用户请求来使用寄存器变量。 但是，出于可移植性考虑，编译器将遵循所有与 register  关键字关联的其他语义。 例如，无法将一元 address-of 运算符 (&  ) 应用于寄存器对象，也无法在数组上使用 register  关键字。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内部级别声明的存储类说明符](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
