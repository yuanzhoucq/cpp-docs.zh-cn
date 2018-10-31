---
title: 编译器警告（等级 1）C4743
ms.date: 11/04/2016
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: d17fd65f1108aab6e3ce97ec75c0ffb899c06cda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441842"
---
# <a name="compiler-warning-level-1-c4743"></a>编译器警告（等级 1）C4743

'*类型*具有不同的大小*file1*和*file2*:*数*并*数量*字节

外部变量中两个文件引用或定义这些文件中具有不同的类型和编译器判定中变量的大小*file1*中的变量的大小不同*file2*.

C + + 可以发出此警告时重要的用例。 如果要声明相同的类型具有相同名称在两个不同的文件，如果这些声明包含虚函数，并声明不相同，编译器可以发出警告 C4744 虚函数表。 警告是因为有两个不同大小的虚拟函数的表相同的类型，并且链接器必须选择其中一个将合并到可执行文件。  有可能，这可能会导致错误的虚拟函数调用程序。

若要解决此警告，请使用相同的类型定义或使用不同的类型或变量的名称。

## <a name="example"></a>示例

此示例包含一个定义的类型。

```
// C4743a.cpp
// compile with: /c
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

## <a name="example"></a>示例

下面的示例生成 C4743。

```
// C4743b.cpp
// compile with: C4743a.cpp /W1 /GL /O2
// C4743 expected
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```