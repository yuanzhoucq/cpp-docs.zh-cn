---
title: 编译器警告（等级1） C4632
ms.date: 11/04/2016
f1_keywords:
- C4632
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
ms.openlocfilehash: 4a24e54b443707775375a2adf833748eae347ce8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052582"
---
# <a name="compiler-warning-level-1-c4632"></a>编译器警告（等级1） C4632

XML 文档注释：文件访问被拒绝：原因

.Xdc 文件的路径（`file`）无效，并且未创建 .xdc 文件。

下面的示例生成 C4632：

```cpp
// C4632.cpp
// compile with: /clr /docv:\\falsedir /LD /W1
// C4632 expected

/// Text for class MyClass.
public ref class MyClass {};
```