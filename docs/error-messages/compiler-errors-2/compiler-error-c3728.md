---
title: 编译器错误 C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165869"
---
# <a name="compiler-error-c3728"></a>编译器错误 C3728

"event"：事件没有引发方法

使用一种语言创建的元数据C#（例如）不允许从定义该事件的类的外部引发事件，而是在[#using](../../preprocessor/hash-using-directive-cpp.md)指令中附带，使用 CLR 编程的可视化C++程序尝试引发该事件。

若要在使用之类的语言开发的程序中引发事件C#，则包含事件的类还需要定义引发事件的公共方法。
