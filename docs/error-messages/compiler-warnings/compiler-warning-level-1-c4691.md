---
title: 编译器警告（等级 1）C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: c194e19c8766b67eb7deef32e7228564cda5f1e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406374"
---
# <a name="compiler-warning-level-1-c4691"></a>编译器警告（等级 1）C4691

type： 在未引用程序集 file，而是使用了当前翻译单元中定义的类型应是引用类型

不引用包含原始类型定义的元数据文件，且编译器所使用的本地类型定义。

在您正在重新生成的情况下*文件*，可以忽略或使用杂注关闭 C4691[警告](../../preprocessor/warning.md)。  也就是说，如果要生成该文件是编译器希望查找的类型定义的文件同名，则可以忽略 C4691。

但是，可能发生意外的行为，如果编译器将使用不是来自同一元数据; 中引用的程序集的定义CLR 类型被类型不仅按类型的名称，还由程序集。  也就是说，从程序集 z.dll 类型 Z 为不同于从程序集 y.dll 类型 Z。

## <a name="example"></a>示例

此示例包含原始类型定义。

```
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>示例

此示例引用 C4691_a.dll 和声明类型 Original_Type 的字段。

```
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>示例

下面的示例生成 C4691。  请注意，此示例包含 Original_Type 定义，并不引用 C4691a.dll。

若要解决，引用包含原始类型定义的元数据文件和删除的局部声明和定义。

```
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```