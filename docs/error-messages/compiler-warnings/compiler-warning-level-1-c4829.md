---
title: 编译器警告（等级 1）C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: ace409cee05650e0dbfbcdd32cd15e85f8dbf006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594163"
---
# <a name="compiler-warning-level-1-c4829"></a>编译器警告（等级 1）C4829

函数 main 的参数可能不正确。 请考虑 intmain (platform:: array\<platform:: string ^ > ^ argv)

某些函数（如 main）不能采用引用类型参数。 虽然编译会成功，但是生成的图像可能不会运行。

以下示例生成 C4829：

```
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829

```