---
title: 编译器错误 C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328096"
---
# <a name="compiler-error-c3728"></a>编译器错误 C3728

event： 事件没有引发方法

创建的元数据一种语言，如C#，不允许使用一个事件，它从其已定义，包括在类的外部引发[#using](../../preprocessor/hash-using-directive-cpp.md)指令和视觉对象C++程序使用 CLR 编程试图引发事件。

若要将提升在 C# 等语言中开发的程序中的事件，包含该事件的类需要还定义一个引发事件的公共方法。