---
title: 编译器错误 C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206656"
---
# <a name="compiler-error-c2220"></a>编译器错误 C2220

警告被视为错误-没有生成对象文件

[/Wx](../../build/reference/compiler-option-warning-level.md)通知编译器将所有警告视为错误。 由于发生了错误，未生成对象或可执行文件。

仅当设置了 **/wx**标志并在编译期间出现警告时，才会出现此错误。 若要纠正此错误，必须消除项目中的每个警告。

### <a name="to-fix-use-one-of-the-following-techniques"></a>若要纠正错误，请使用以下方法之一

- 解决导致项目中出现警告的问题。

- 以较低的警告等级进行编译-例如，使用 **/W3**而不是 **/W4**。

- 使用[警告](../../preprocessor/warning.md)杂注禁用或取消显示特定警告。

- 不要使用 **/wx**进行编译。
