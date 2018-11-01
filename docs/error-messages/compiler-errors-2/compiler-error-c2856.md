---
title: 编译器错误 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499601"
---
# <a name="compiler-error-c2856"></a>编译器错误 C2856

\#杂注 hdrstop #if 块内不能为

`hdrstop`杂注不能放置在条件编译块的主体内。

移动`#pragma hdrstop`语句未包含在一个区域`#if/#endif`块。