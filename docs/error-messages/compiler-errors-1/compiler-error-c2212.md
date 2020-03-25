---
title: 编译器错误 C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: bf478c96e76a4fe139caee79f497a0abe7f70824
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206670"
---
# <a name="compiler-error-c2212"></a>编译器错误 C2212

"identifier"： __based 不可用于指向函数的指针

指向函数的指针不能 `__based`声明。 如果需要基于代码的数据，请使用 `__declspec` 关键字或 `data_seg` 杂注。
