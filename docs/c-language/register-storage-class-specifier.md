---
title: "register 存储类说明符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95c06471b7d8ea60754c29a9bde3159174e9c194
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="register-storage-class-specifier"></a>register 存储类说明符
**Microsoft 专用**  
  
 Microsoft C/C++ 编译器不会按照用户请求来使用寄存器变量。 但是，出于可移植性考虑，编译器将遵循所有与 register 关键字关联的其他语义。 例如，无法将一元 address-of 运算符 (&) 应用于寄存器对象，也无法在数组上使用 register 关键字。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [内部级别声明的存储类说明符](../c-language/storage-class-specifiers-for-internal-level-declarations.md)