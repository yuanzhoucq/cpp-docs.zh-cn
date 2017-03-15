---
title: "CRT 初始化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRT 初始化 [C++]"
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# CRT 初始化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题描述 CRT 如何初始化全局状态用本机代码。  
  
 默认方式，链接器包括 CRT 库，提供自己的启动代码。  启动此代码初始化 CRT 库，调用全局初始值设定项，然后调用。控制台应用程序用户提供的 `main` 函数。  
  
## 初始化全局对象  
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
  
 根据标准，C\/C\+\+ `func()`，在 `main()` 完成之前，必须调用。  但谁调用了它？  
  
 一种确定此将在 `func()`处设置断点，调试应用程序并且检查堆栈。  因为CRT源代码包含带有 Visual Studio，这也是可能的。  
  
 在您浏览时堆栈上的函数，您发现 CRT 通过函数指针列表循环并调用每一个。  这些函数类似于 `func()` 或类的实例构造函数。  
  
 CRT 来获取函数指针列表从 Visual C\+\+ 编译器中。  在编译器显示全局初始化表达式时，它会在 `.CRT$XCU` 部分的动态初始值设定 \(其中 `CRT` 为部分名称，`XCU` 是组\)。  \(当 main.cpp编译成C\+\+ 文件而不是C 文件时\)若要获得这些动态初始值设定项列表中运行命令 **dumpbin \/all main.obj**，然后搜索 `.CRT$XCU` 节。  它类似于以下内容：  
  
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
  
-   `.CRT$XCA`中的`__xc_a`  
  
-   `.CRT$XCZ`中的`__xc_z`  
  
 两组没有任何其他符号定义除 `__xc_a` 和 `__xc_z`。  
  
 现在当链接器读取各种 `.CRT` 组中，将一节中将它们按字母顺序对它们。  这意味着在 `.CRT$XCU`将 Visual C\+\+ 编译器\) 的用户定义的表达式初始化全局 \(始终是在 `.CRT$XCA` 之后但在 `.CRT$XCZ`之前。  
  
 节将类似于以下内容：  
  
```  
.CRT$XCA  
            __xc_a  
.CRT$XCU  
            Pointer to Global Initializer 1  
            Pointer to Global Initializer 2  
.CRT$XCZ  
            __xc_z  
```  
  
 因此，CRT 库使用 `__xc_a`，并且确定全局初始化表达式的开始和结尾。`__xc_z` 列出由于它们在内存中的布局方式，在图像加载后执行。  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)