---
title: 编译器警告（等级 1）C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: f0d1df0a383b6646d52fc2babc53ca656d49ace6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428192"
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910

\<标识符 >: __declspec （dllexport） 和 extern 在显式实例化上不兼容

名为的显式模板实例化*\<标识符 >* 由已修改`__declspec(dllexport)`和`extern`关键字。 但是，这些关键字互斥。 `__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。

## <a name="see-also"></a>请参阅

[显式实例化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般规则和限制](../../cpp/general-rules-and-limitations.md)