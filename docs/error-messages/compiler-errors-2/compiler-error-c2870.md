---
title: 编译器错误 C2870 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2870
dev_langs:
- C++
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47101cbc2fb1be48ba54166b9c6ef99fc0c6c35e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073871"
---
# <a name="compiler-error-c2870"></a>编译器错误 C2870

name： 命名空间定义必须出现在文件范围内或在另一个命名空间定义立即出现

定义命名空间`name`不正确。 必须在文件范围内 （之外的所有块和类） 定义的命名空间或立即在另一个命名空间内。

下面的示例生成 C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```