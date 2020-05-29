---
title: 编译器警告（等级 1）C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a556fbffad41d04b3eb0ea1acfd5e8739ddd5b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186798"
---
# <a name="compiler-warning-level-1-c4399"></a>编译器警告（等级 1）C4399

> "*symbol*"：用/clr： pure 编译时，每进程符号不应标记为 __declspec （dllimport）

## <a name="remarks"></a>备注

**/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

本机映像中的数据或具有本机和 CLR 构造的映像的数据无法导入到纯映像。 若要解决此警告，请用 **/clr** （而非 **/clr： pure**）进行编译或删除 `__declspec(dllimport)`。

## <a name="example"></a>示例

下面的示例生成 C4399。

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
