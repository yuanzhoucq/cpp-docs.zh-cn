---
title: init_seg 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 5e57ea0eedfc1df6e196391c5edd3acfbad0a7c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221002"
---
# <a name="init_seg-pragma"></a>init_seg 杂注

**C++相关**

指定影响启动代码的执行顺序的关键字或代码部分。

## <a name="syntax"></a>语法

> **#pragma init_seg (** {**编译器** | **lib** | **用户**|"*节名*" [ **,** *函数名*]} **)**

## <a name="remarks"></a>备注

术语 "*段*" 和 "*节*" 在本文中具有相同的含义。

由于有时代码需要初始化全局静态对象, 因此必须指定何时构造对象。 特别要注意的是, 在动态链接库 (Dll) 或需要初始化的库中使用**init_seg**杂注非常重要。

**Init_seg**杂注的选项如下:

**编译程序**\
保留以供 Microsoft C 运行库初始化使用. 首先构造该组中的对象。

**lib**\
可用于第三方类库供应商的初始化。 此组中的对象将在标记为**编译器**之后但在任何其他对象之前构造。

**用户**\
可供任何用户使用。 最后构造此组中的对象。

*节名称*\
允许初始化部分的显式规范。 用户指定的*节名*中的对象不是隐式构造的。 但是, 它们的地址位于按*节名称*命名的部分中。

所赋的*节名称*将包含指向 helper 函数的指针, 这些函数将构造在该模块中的杂注之后声明的全局对象。

有关创建部分时不应使用的名称的列表, 请参阅[/SECTION](../build/reference/section-specify-section-attributes.md)。

*func-名称*\
指定在程序退出时为替换 `atexit` 而调用的函数。 此 helper 函数还通过指向全局对象的析构函数的指针调用[atexit](../c-runtime-library/reference/atexit.md) 。 如果以杂注形式指定函数标识符，

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

则将调用您的函数而不是 C 运行库的 `atexit`。 它使您可以生成在您准备好销毁对象时要调用的析构函数的列表。

如果需要延迟初始化（例如，在 DLL 中），则可以选择显式指定节名称。 然后, 你的代码必须调用每个静态对象的构造函数。

`atexit` 替换的标识符周围没有引号。

您的对象仍将被置于由其他`XXX_seg`杂注定义的部分中。

在模块中声明的对象不会由 C 运行时自动初始化。 你的代码必须执行初始化。

默认情况下，`init_seg` 部分是只读的。 如果节名称为, `.CRT`则编译器会将属性以无提示方式更改为只读, 即使它标记为读取、写入。

不能在翻译单元中多次指定**init_seg** 。

即使您的对象没有用户定义的构造函数 (在代码中显式定义的构造函数), 编译器可能会为您生成一个。 例如, 可以创建一个绑定 v-表指针。 如果需要, 你的代码将调用编译器生成的构造函数。

## <a name="example"></a>示例

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
