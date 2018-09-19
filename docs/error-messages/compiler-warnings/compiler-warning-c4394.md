---
title: 编译器警告 C4394 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99200dd01db610aa558e8a9df18b7afacdf3d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099496"
---
# <a name="compiler-warning-c4394"></a>编译器警告 C4394

function: per-appdomain 符号不应该用 __declspec （dllexport） 标记

使用标记的函数[appdomain](../../cpp/appdomain.md) `__declspec`修饰符编译为 MSIL （不，为本机），并导出表 ([导出](../../windows/export.md)`__declspec`修饰符) 不支持对托管的函数。

您可以将托管函数声明为具有公共可访问性。 有关详细信息，请参阅[键入可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)并[成员的可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。

C4394 始终作为错误发出。  您可以关闭此警告，其中包含`#pragma warning`或 **/wd**; 请参阅[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 / w4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd、 / /we、 /wo、 /Wv、 /WX （警告级别）](../../build/reference/compiler-option-warning-level.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C4394。

```
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```