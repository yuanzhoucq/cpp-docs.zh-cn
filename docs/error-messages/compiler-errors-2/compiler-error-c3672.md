---
title: 编译器错误 C3672
ms.date: 11/04/2016
f1_keywords:
- C3672
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
ms.openlocfilehash: 36048f3e4b8cc1be3e766f11b5c131513a3365da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214999"
---
# <a name="compiler-error-c3672"></a>编译器错误 C3672

伪析构函数表达式只能用作函数调用的一部分

未正确调用析构函数。  有关详细信息，请参阅[析构函数](../../cpp/destructors-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C3672。

```
// C3672.cpp
template<typename T>
void f(T* pT) {
   &pT->T::~T;   // C3672
   pT->T::~T();   // OK
};

int main() {
   int i;
   f(&i);
}
```