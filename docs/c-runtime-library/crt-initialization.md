---
title: CRT 初始化
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 980d94b29d31d8eea910fbdb171a0ae8df1dccca
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750031"
---
# <a name="crt-initialization"></a>CRT 初始化

本主题介绍 CRT 如何在本机代码中初始化全局状态。

默认情况下，链接器包括 CRT 库，此库提供其自己的启动代码。 此启动代码初始化 CRT 库，调用全局初始值设定项，然后调用用于控制台应用程序的用户提供的 `main` 函数。

## <a name="initializing-a-global-object"></a>初始化全局对象

考虑下列代码：

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

根据 C/C++ 标准，在执行 `main()` 前必须调用 `func()`。 但哪个项来调用它呢？

确定这一点的一个方法是在 `func()` 中设置断点，调试应用程序并检查堆栈。 由于 CRT 源代码是 Visual Studio 附带的，因此可以这样做。

在堆栈上浏览函数时，您将发现 CRT 正在循环访问函数指针的列表并在遇到每个指针时对其进行调用。 这些函数类似于 `func()` 或类实例的构造函数。

CRT 从 Visual C++ 编译器中获取函数指针的列表。 当编译器发现全局初始值时，它将在 `.CRT$XCU` 部分（其中，`CRT` 是部分名称，`XCU` 是组名称）中生成一个动态初始值设定项。 若要获取这些动态初始值设定项的列表，请运行命令 dumpbin /all main.obj，然后搜索 `.CRT$XCU` 部分（在将 main.cpp 作为 C++ 文件而不是 C 文件编译时）。 它将类似于以下内容：

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                                Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  ------
00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT 定义两个指针：

- `__xc_a`中的`.CRT$XCA`

- `__xc_z`中的`.CRT$XCZ`

除了 `__xc_a` 和 `__xc_z` 之外，两个组未定义任何其他符号。

现在，当链接器读取各种 `.CRT` 组时，它会将这些组合并在一个部分中并按字母顺序对其进行排序。 这表示用户定义的全局初始值设定项（Visual C++ 编译器将其置于 `.CRT$XCU` 中）将始终出现在 `.CRT$XCA` 之后和 `.CRT$XCZ` 之前。

此部分类似于以下内容：

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

CRT 库会使用 `__xc_a` 和 `__xc_z` 来确定全局初始值设定项列表的开头和结尾，原因在于这些设定项在图像加载后在内存中布局的方式。

## <a name="see-also"></a>请参阅

[CRT 库功能](../c-runtime-library/crt-library-features.md)
