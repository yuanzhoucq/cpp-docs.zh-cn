---
title: 编译器错误 C2605
ms.date: 11/04/2016
f1_keywords:
- C2605
helpviewer_keywords:
- C2605
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
ms.openlocfilehash: dfa221500d27e71cdbe1ab581eec346c0f268b66
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737876"
---
# <a name="compiler-error-c2605"></a>编译器错误 C2605

“name”: 此方法是托管或 WinRT 类中的保留方法

某些名称由编译器保留用于内部函数。  有关详细信息，请参阅[析构函数和终结](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)器。

## <a name="example"></a>示例

以下示例生成 C2605。

```cpp
// C2605.cpp
// compile with: /clr /c
ref class R {
protected:
   void Finalize() {}   // C2605
};
```
