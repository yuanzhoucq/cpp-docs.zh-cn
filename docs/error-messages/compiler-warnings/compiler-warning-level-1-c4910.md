---
title: 编译器警告（等级 1）C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: dc5feb3613e45134a08e493b397eb738fffee8a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174773"
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910

"\<标识符 >"： "__declspec （dllexport）" 和 "extern" 在显式实例化上不兼容

名为 *\<标识符 >* 的显式模板实例化由 `__declspec(dllexport)` 和 `extern` 关键字进行修改。 但是，这些关键字互斥。 `__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。

## <a name="see-also"></a>另请参阅

[显式实例化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般规则和限制](../../cpp/general-rules-and-limitations.md)
