---
title: 编译器警告（等级 1）C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 49cbbf3369fc4765d93e67e2dca84a4d975560d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242879"
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910

\<标识符 >: __declspec （dllexport） 和 extern 在显式实例化上不兼容

名为的显式模板实例化*\<标识符 >* 由已修改`__declspec(dllexport)`和`extern`关键字。 但是，这些关键字互斥。 `__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。

## <a name="see-also"></a>请参阅

[显式实例化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般规则和限制](../../cpp/general-rules-and-limitations.md)