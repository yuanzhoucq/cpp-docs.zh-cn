---
title: "使用 __declspec(dllimport) 导入函数调用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__declspec"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) 关键字 [C++]"
  - "dllimport 特性 [C++], 函数调用导入"
  - "函数调用 [C++], 导入"
  - "导入函数调用 [C++]"
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用 __declspec(dllimport) 导入函数调用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例显示如何使用 **\_declspec\(dllimport\)** 将函数调用从 DLL 导入到应用程序中。  假定 `func1` 是驻留在某个 DLL 中的函数，而此 DLL 与包含“主”函数的 .exe 文件是分开的。  
  
 不使用 **\_\_declspec\(dllimport\)**，给出此代码：  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 编译器生成类似下面的代码：  
  
```  
call func1  
```  
  
 链接器将调用翻译成下面的内容：  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 如果 `func1` 存在于另一个 DLL 中，链接器将无法直接解析此函数，因为它无法得知 `func1` 的地址。  在 16 位环境中，链接器将此代码地址添加到 .exe 文件中的某个列表中，而加载程序在运行时会用正确的地址修补该列表。  在 32 位和 64 位环境中，链接器可生成一个知道其地址的 thunk。  在 32 位环境中，thunk 类似如下所示：  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 其中，`imp_func1` 是 `func1` 的槽在 .exe 文件的导入地址表中的地址。  这样，链接器就知道了所有的地址。  加载程序只需在加载时更新 .exe 文件的导入地址表，一切就会正常进行。  
  
 因此，使用 **\_\_declspec\(dllimport\)** 更好，因为链接器不生成不必要的 thunk。  thunk 使代码变大（在 RISC 系统上代码它可能是若干指令），并且会降低缓存性能。  如果通知编译器函数在 DLL 中，编译器会为您生成间接调用。  
  
 因此，现在此代码：  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 生成此指令：  
  
```  
call DWORD PTR __imp_func1  
```  
  
 没有 thunk 和 `jmp` 指令，所以代码更小且更快。  
  
 另一方面，对于 DLL 内部的函数调用，您希望不必使用间接调用。  您已经知道函数的地址。  由于间接调用前需要时间和空间来加载和存储函数的地址，因此直接调用总是更快，而且所需的空间也总是更小。  当从 DLL 本身外部调用 DLL 时，您仅希望使用 **\_\_declspec\(dllimport\)**。  生成某个 DLL 时不要对该 DLL 的内部函数使用 **\_\_declspec\(dllimport\)**。  
  
## 请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)