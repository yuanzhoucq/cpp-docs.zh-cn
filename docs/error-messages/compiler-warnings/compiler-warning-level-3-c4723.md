---
title: 编译器警告（等级 3）C4723
description: 描述 MSVC 编译器警告 C4723，以使其可能被零除。
ms.date: 07/08/2020
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: 57a5758d8a3198d7701bdead2e1bbe567b72701a
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180989"
---
# <a name="compiler-warning-level-3-c4723"></a>编译器警告（等级 3）C4723

> `potential divide by 0`

除法运算中的第二个操作数在编译时计算为零，并提供未定义的结果。

仅当启用了优化时才会发出此警告。

编译器可能生成了零操作数。
