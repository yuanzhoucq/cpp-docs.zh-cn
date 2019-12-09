---
title: 编译器错误 C3459
ms.date: 11/04/2016
f1_keywords:
- C3459
helpviewer_keywords:
- C3459
ms.assetid: 3d290a20-d313-4c07-9bd8-c5c159cb169f
ms.openlocfilehash: 7fe21414fcadef13b7af3acf4f8e1635fb12802e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756638"
---
# <a name="compiler-error-c3459"></a>编译器错误 C3459

“attribute”：特性只允许出现在类索引器上（默认索引属性）

错误地使用了设计为应用于类索引器属性的特性。

有关详细信息，请参阅[如何：在/cli 中C++使用属性](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3459。

```cpp
// C3459.cpp
// compile with: /clr /c
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3459
   property int Prop;
};

// OK
public ref class MyString2 {
   array<int>^ MyArr;
public:
   MyString2() {
      MyArr = gcnew array<int>(5);
   }

   [System::Runtime::CompilerServices::IndexerName("Chars")]   // OK
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};
```
