---
title: 编译器错误 C3669 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3669
dev_langs:
- C++
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7588ec3862c914fd998a7b5a3f59ff4d0bb5bbf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088649"
---
# <a name="compiler-error-c3669"></a>编译器错误 C3669

member： 重写的说明符 override 不允许在静态成员函数或构造函数

重写未正确指定。 有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3669。

```
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```