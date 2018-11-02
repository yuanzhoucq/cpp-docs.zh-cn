---
title: 命令行警告 D9043
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 62834c5f245bc1c0f6197638e4608b7fe71e7eb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586025"
---
# <a name="command-line-warning-d9043"></a>命令行警告 D9043

无效的值为 compiler_option; warning_level假定 '4999';代码分析警告与警告等级无关

## <a name="example"></a>示例

下面的示例生成 C9043。

```
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```