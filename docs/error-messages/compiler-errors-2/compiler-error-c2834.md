---
title: 编译器错误 C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: fb4a0e6f3f6ec227b978ae0b7d3864b2134de986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406816"
---
# <a name="compiler-error-c2834"></a>编译器错误 C2834

operator operator 必须是全局限定

`new`和`delete`运算符被绑定到类驻留位置。 不能使用范围解析的某个版本`new`或`delete`从另一个类。 若要实现的多个窗体`new`或`delete`运算符，用额外的形参创建运算符版本。