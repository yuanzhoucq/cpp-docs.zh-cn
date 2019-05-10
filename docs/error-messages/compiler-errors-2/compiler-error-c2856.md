---
title: 编译器错误 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406842"
---
# <a name="compiler-error-c2856"></a>编译器错误 C2856

\#杂注 hdrstop #if 块内不能为

`hdrstop`杂注不能放置在条件编译块的主体内。

移动`#pragma hdrstop`语句未包含在一个区域`#if/#endif`块。