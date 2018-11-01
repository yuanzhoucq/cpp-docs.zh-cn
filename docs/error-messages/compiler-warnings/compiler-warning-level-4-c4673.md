---
title: 编译器警告（等级 4）C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: ceaa5cd647dfb527713613b9ce3b5cd81a780fd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657725"
---
# <a name="compiler-warning-level-4-c4673"></a>编译器警告（等级 4）C4673

引发以下类型的 identifier 不会被视为在 catch 站点

不能在中处理引发对象**捕获**块。 不能处理每种类型是紧跟包含此警告的行的错误输出中列出。 每个未处理的类型都有其自己的警告。 读取的每个特定类型的详细信息的警告。

下面的示例生成 C4673:

```
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```