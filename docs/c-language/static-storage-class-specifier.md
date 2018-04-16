---
title: "static 存储类说明符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c957b78eeb506e9f1f91a670cf5cc4d52ad72878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="static-storage-class-specifier"></a>静态存储类说明符
使用 **static** 存储类说明符在内部级别声明的变量具有全局生存期，但它仅在声明它的块中可见。 对于常量字符串，使用 **static** 会很有用，因为它减少了频繁初始化经常调用的函数的开销。  
  
## <a name="remarks"></a>备注  
如果不显式初始化 **static** 变量，则默认情况下它将初始化为 0。 在函数内，**static** 会导致存储被分配并用作定义。 内部静态变量仅提供对单个函数可见的私有永久存储。  
  
## <a name="see-also"></a>请参阅  
[C 存储类](c-storage-classes.md)  
[存储类 (C++)](../cpp/storage-classes-cpp.md)  