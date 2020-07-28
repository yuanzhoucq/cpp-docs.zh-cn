---
title: 编译器警告（等级 1）C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: b17df9d7a9997e5d8ef37a4721de8693968cbbdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214446"
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910

" \<identifier> "： "__declspec （dllexport）" 和 "extern" 在显式实例化上不兼容

名为的显式模板实例化 *\<identifier>* 由 `__declspec(dllexport)` 和关键字进行修改 **`extern`** 。 但是，这些关键字互斥。 `__declspec(dllexport)`关键字表示实例化模板类，而 **`extern`** 关键字表示不要自动实例化模板类。

## <a name="see-also"></a>另请参阅

[显式实例化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般规则和限制](../../cpp/general-rules-and-limitations.md)
