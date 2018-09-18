---
title: 错误 C1047 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1983fa0a18667d98f84dfe5049afd4e872d87d93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021585"
---
# <a name="fatal-error-c1047"></a>错误 C1047

对象或库文件“file”是使用比创建其他对象所用编译器旧的编译器创建的；请重新生成旧的对象和库

当使用 **/LTCG** 生成的对象文件或库链接在一起，而这些对象文件或库是用不同版本的 Visual C++ 工具集生成的，则会导致 C1047。

当你开始使用新版本的编译器，而不完全重新生成现有对象文件或库时，可能出现这种情况。

若要解决 C1047，请重新生成所有对象文件或库。