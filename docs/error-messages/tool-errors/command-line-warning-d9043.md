---
title: 命令行警告 D9043 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9043
dev_langs:
- C++
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d29371e147c693b2aa49f8dcf838841af3c75c8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031854"
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