---
title: 编译器错误 C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 45a140d3fd5f510ee2434950ca3c4b47c0756d75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385493"
---
# <a name="compiler-error-c3893"></a>编译器错误 C3893

var： 只允许在类 type_name 的实例构造函数的 initonly 数据成员的左值使用

静态[initonly](../../dotnet/initonly-cpp-cli.md)数据成员只能在静态构造函数采用其地址。

实例 （非静态） initonly 数据成员只能在实例 （非静态） 构造函数采用其地址。

下面的示例生成 C3893:

```
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```