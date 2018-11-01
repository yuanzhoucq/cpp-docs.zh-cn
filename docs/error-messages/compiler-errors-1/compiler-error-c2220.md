---
title: 编译器错误 C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603406"
---
# <a name="compiler-error-c2220"></a>编译器错误 C2220

警告视为错误-没有生成的对象文件

[/WX](../../build/reference/compiler-option-warning-level.md)告知编译器将所有警告视为错误。 由于发生了错误，未生成对象或可执行文件。

时，此错误仅出现 **/WX**设置标志并且编译期间，出现一条警告。 若要纠正此错误，必须消除项目中的每个警告。

### <a name="to-fix-use-one-of-the-following-techniques"></a>若要纠正错误，请使用以下方法之一

- 解决导致项目中出现警告的问题。

- 在较低警告等级进行编译-例如，使用 **/W3**而不是 **/w4**。

- 使用[警告](../../preprocessor/warning.md)杂注来禁用或禁止特定警告。

- 不要使用 **/WX**进行编译。