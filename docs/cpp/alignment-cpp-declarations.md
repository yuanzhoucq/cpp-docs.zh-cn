---
title: 对齐方式 （C++ 声明） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f39fe0cf3706a67e2aa42aa89de5914808e9cec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="alignment-c-declarations"></a>对齐方式（C++ 声明）
C + + 的低级功能之一是能够指定内存中对象的精确对齐方式，以最大限度利用特定的硬件体系结构。 默认情况下，编译器根据其大小值来对齐类和结构成员：bool 和 char 都对齐一个 1 字节边界、短整型两个字节、整型四个字节，长整型、双精度型和长双精度型八个字节。 在大多数情况下，你永远无需注意对齐方式，因为默认对齐方式已经是最佳的。 但是，在某些情况下，你可以通过指定数据结构的自定义对齐方式获得显著的性能提升或节约内存。 在 Visual Studio 2015 之前，可以使用 Microsoft 专用关键字 __alignof 和 declspec(alignas) 来指定大于默认值的对齐方式。 从 Visual Studio 2015 开始，应使用 C++ 11 标准关键字[alignof 和 alignas](../cpp/alignof-and-alignas-cpp.md)获得最大代码可移植性。 新关键字实质上以与 Microsoft 专用扩展相同的方式运行，这些扩展的文档也适用于这些新关键字。 请参阅[__alignof 运算符](../cpp/alignof-operator.md)和[对齐](../cpp/align-cpp.md)有关详细信息。 C++ 标准不指定小于目标平台中，默认的编译器的边界上对齐，因此仍需要使用 Microsoft #pragma 的装箱行为[包](../preprocessor/pack.md)在这种情况下。  
  
 C++ 标准库提供[aligned_storage 类](../standard-library/aligned-storage-class.md)为具有自定义对齐方式的数据结构分配内存和[aligned_union 类](../standard-library/aligned-union-class.md)用于指定具有联合的对齐方式非普通构造函数或析构函数。  
  
## <a name="about-alignment"></a>关于对齐方式  
 对齐方式是内存地址的一个属性，表示为数字地址对 2 的幂次方取模。 例如，地址 0x0001103F 对 4 取模为 3 ；则该地址将对齐到 4n+3，其中 4 表示选择的 2 的幂次方。 地址的对齐方式取决于选择的 2 的幂次方。 相同的地址对 8 取模为 7。 如果一个地址的对齐方式是 Xn+0，它将对齐到 X。  
  
 CPU 执行作用于内存中所存储数据的指令，数据在内存中用地址标识。 除其地址外，单个基准也具有大小。 如果一个基准的地址对齐到其大小，则称它为自然对齐，否则为未对齐。 例如，如果地址用于标识其对齐到 8，则自然对齐 8 字节浮点基准。  
  
 数据 alignmentDevice 编译器的编译器处理尝试以防止数据未对齐的方式分配数据。  
  
 对于简单的数据类型，编译器将分配是数据类型的大小（以字节为单位）的倍数的地址。 因此，编译器将地址分配给类型为 long 且是 4 的倍数的变量，并将地址的最底部两位设置为零。  
  
 此外，编译器以自然对齐结构的每一个元素的方式填充结构。 考虑下面代码示例中的结构 struct x_：  
  
```  
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 编译器填充此结构以自然强制实施对齐方式。  
  
 下面的代码示例演示编译器如何将填充的结构置于内存中：复制  
  
```  
// Shows the actual memory layout  
struct x_  
{  
   char a;            // 1 byte  
   char _pad0[3];     // padding to put 'b' on 4-byte boundary  
   int b;            // 4 bytes  
   short c;          // 2 bytes  
   char d;           // 1 byte  
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4  
}  
  
```  
  
1.  两个声明都将 sizeof(struct x_) 作为 12 个字节返回。  
  
2.  第二个声明包括两个填充元素：  
  
3.  char _pad0 [3]，对齐 4 字节边界上的整型 b 成员  
  
4.  char _pad1 [1]，对齐结构 struct _x bar[3] 的数组元素；  
  
5.  填充以允许自然访问的方式对齐 bar[3] 的元素。  
  
 下面的代码示例显示 bar[3] 的数组布局：  
  
```  
adr offset   element  
------   -------  
0x0000   char a;         // bar[0]  
0x0001   char pad0[3];  
0x0004   int b;  
0x0008   short c;  
0x000a   char d;  
0x000b   char _pad1[1];  
  
0x000c   char a;         // bar[1]  
0x000d   char _pad0[3];  
0x0010   int b;  
0x0014   short c;  
0x0016   char d;  
0x0017   char _pad1[1];  
  
0x0018   char a;         // bar[2]  
0x0019   char _pad0[3];  
0x001c   int b;  
0x0020   short c;  
0x0022   char d;  
0x0023   char _pad1[1];  
  
```  
  
## <a name="see-also"></a>请参阅  
 [数据结构对齐方式](http://en.wikipedia.org/wiki/Data_structure_alignment)