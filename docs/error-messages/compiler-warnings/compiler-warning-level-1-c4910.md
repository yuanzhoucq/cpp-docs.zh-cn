---
title: 编译器警告（等级 1）C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: a3f29cb895da8c06ed43dd5c9956426f3f6014f1
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810714"
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910

"\<标识符 >"： "__declspec （dllexport）" 和 "extern" 在显式实例化上不兼容

名为 *\<标识符 >* 的显式模板实例化由 `__declspec(dllexport)` 和 `extern` 关键字进行修改。 但是，这些关键字互斥。 `__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。

## <a name="see-also"></a>另请参阅

[显式实例化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般规则和限制](../../cpp/general-rules-and-limitations.md)