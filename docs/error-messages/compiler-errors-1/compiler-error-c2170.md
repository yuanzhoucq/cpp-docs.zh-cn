---
title: 编译器错误 C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 04d41a50bc0d5e811e47e5f9d146362a543f26f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174674"
---
# <a name="compiler-error-c2170"></a>编译器错误 C2170

identifier： 没有声明为一个函数，不能为内部函数

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 杂注`intrinsic`用于与函数之外的项。

1. 杂注`intrinsic`用于没有内部形式的函数。