---
title: 错误 C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 5ab98c46d60d15cdcb6de22aa922d62453d41880
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204485"
---
# <a name="fatal-error-c1047"></a>错误 C1047

对象或库文件“file”是使用比创建其他对象所用编译器旧的编译器创建的；请重新生成旧的对象和库

当使用 **/LTCG** 生成的对象文件或库链接在一起，而这些对象文件或库是用不同版本的 Visual C++ 工具集生成的，则会导致 C1047。

当你开始使用新版本的编译器，而不完全重新生成现有对象文件或库时，可能出现这种情况。

若要解决 C1047，请重新生成所有对象文件或库。
