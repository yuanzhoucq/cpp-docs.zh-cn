---
title: 编译器错误 C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397622"
---
# <a name="compiler-error-c2129"></a>编译器错误 C2129

静态函数 function 声明但未定义

对前向引用`static`永远不会定义的函数。

一个`static`必须在文件范围内定义函数。 如果在另一个文件中定义函数，则它必须声明`extern`。