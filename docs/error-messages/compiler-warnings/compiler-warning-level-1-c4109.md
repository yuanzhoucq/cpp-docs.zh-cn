---
title: 编译器警告（等级 1）C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: b6b6c0f182aff9bdb4a5e4e7d35dfd111e11e079
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626300"
---
# <a name="compiler-warning-level-1-c4109"></a>编译器警告（等级 1）C4109

意外的标识符“identifier”

忽略包含意外标识符的杂注。

## <a name="example"></a>示例

```cpp
// C4109.cpp
// compile with: /W1 /LD
#pragma init_seg( abc ) // C4109
```