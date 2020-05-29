---
title: 编译器警告（等级 1）C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 8065129e20b627eb387421455527f6aaec3fdc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175371"
---
# <a name="compiler-warning-level-1-c4691"></a>编译器警告（等级 1）C4691

"type"：引用的类型在未引用的程序集 "file" 中应为，而在当前使用的翻译单元中定义的类型为。

未引用包含原始类型定义的元数据文件，并且编译器正在使用本地类型定义。

在重新生成*文件*的情况下，可以忽略 C4691 或关闭杂注[警告](../../preprocessor/warning.md)。  也就是说，如果所生成的文件与编译器希望在其中查找类型定义的文件相同，则可以忽略 C4691。

但是，如果编译器使用的定义不是在元数据中引用的同一程序集，则可能会出现意外行为;CLR 类型不仅类型化，还会由程序集类型的名称键入。  也就是说，程序集 z 中的类型 Z 不同于程序集 y 的类型 Z。

## <a name="example"></a>示例

此示例包含原始类型定义。

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>示例

此示例引用 C4691_a，并声明 Original_Type 类型的字段。

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>示例

下面的示例生成 C4691。  请注意，此示例包含 Original_Type 的定义，并且不引用 C4691a。

若要解决此问题，请引用包含原始类型定义的元数据文件，并删除本地声明和定义。

```cpp
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
