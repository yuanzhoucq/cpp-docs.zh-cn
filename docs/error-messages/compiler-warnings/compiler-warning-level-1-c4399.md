---
title: 编译器警告（等级 1）C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: 56fe0f314142d873fc02136bc2c3fe65e71f4dda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408337"
---
# <a name="compiler-warning-level-1-c4399"></a>编译器警告（等级 1）C4399

> '*符号*: per-process 符号不应该用 __declspec （dllimport） 时使用 /clr 编译标记： pure

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

从本机映像或映像，具有本机和 CLR 构造的数据不导入到纯映像。 若要解决此警告，编译与 **/clr** (不 **/clr: pure**) 或删除`__declspec(dllimport)`。

## <a name="example"></a>示例

下面的示例生成 C4399。

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```