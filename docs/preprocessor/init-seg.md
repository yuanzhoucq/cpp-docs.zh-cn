---
title: init_seg
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 801496739fd9bd2b8a14e699ca4da9fe79f3a28d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026625"
---
# <a name="initseg"></a>init_seg

**C++ 专用**

指定影响启动代码的执行顺序的关键字或代码部分。

## <a name="syntax"></a>语法

```
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )
```

## <a name="remarks"></a>备注

这些术语的含义*段*并*部分*是本主题中可互换的。

由于全局静态对象的初始化可能涉及执行代码，你必须指定用于定义对象的构造时间的关键字。 特别是，务必使用**init_seg**杂注中动态链接库 (Dll) 或需要初始化的库。

为选项**init_seg**杂注是：

*编译器*<br/>
保留以供 Microsoft C 运行库初始化使用. 首先构造该组中的对象。

*lib*<br/>
可用于第三方类库供应商的初始化。 后那些已标记为构造此组中的对象*编译器*但之前的任何其他内容。

*用户*<br/>
可供任何用户使用。 最后构造此组中的对象。

*节名称*允许初始化部分的显式规范。 在用户指定的对象*节名称*不隐式构造; 但将其地址放置在命名的节*节名称*。

您提供的节名称将包含指向 helper 函数的指针，这些函数将构造在杂注后的模块中声明的全局对象。

创建一个部分时，不应使用的名称的列表，请参阅[/section](../build/reference/section-specify-section-attributes.md)。

*func 名称*指定一个函数，来代替调用`atexit`在程序退出时。 此帮助程序函数还将调用[atexit](../c-runtime-library/reference/atexit.md)用一个指针指向全局对象的析构函数。 如果以杂注形式指定函数标识符，

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

则将调用您的函数而不是 C 运行库的 `atexit`。 这允许您生成在准备好销毁对象时要调用的析构函数的列表。

如果需要延迟初始化（例如，在 DLL 中），则可以选择显式指定节名称。 然后，您必须为每个静态对象调用构造函数。

`atexit` 替换的标识符周围没有引号。

您的对象仍放置在由其他 XXX_seg 杂注定义的节中。

模块中声明的对象将不会由 C 运行时自动初始化。 您需要自行执行该操作。

默认情况下，`init_seg` 部分是只读的。 如果节的名称是 .CRT，则编译器将在无提示的情况下将特性更改为只读，即使它被标记为读写。

不能指定**init_seg**多次在翻译单元中。

即使您的对象没有用户定义的构造函数（未在代码中显式定义的构造函数），编译器也会生成一个构造函数（例如，绑定 v-表指针）。 因此，你的代码必须调用编译器生成的构造函数。

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

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)