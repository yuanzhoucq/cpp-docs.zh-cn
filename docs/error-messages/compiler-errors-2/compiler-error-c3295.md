---
title: 编译器错误 C3295 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3295
dev_langs:
- C++
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8210aacf60c4c53faf50278e7494c90c58aa67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076419"
---
# <a name="compiler-error-c3295"></a>编译器错误 C3295

“#pragma pragma”只能在全局范围或命名空间范围上使用

部分杂注不能在函数中使用。  请参阅[杂注指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)有关详细信息。

## <a name="example"></a>示例

以下示例生成 C3295。

```
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```