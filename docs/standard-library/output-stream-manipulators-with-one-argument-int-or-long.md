---
title: 带有一个自变量（int 或 long）的输出流操控器
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 203797eef95e3dab0c079e35baefcea99c3b966d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217657"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>带有一个自变量（int 或 long）的输出流操控器

iostream 类库提供用于创建参数化操控器的一组宏。 使用单个 or 参数的操控器 **`int`** **`long`** 是一种特殊情况。 若要创建接受单个 **`int`** 或 **`long`** 自变量（如）的输出流操控器 `setw` ，则必须使用在中定义的 _Smanip 宏 \<iomanip> 。 此示例定义了向流中插入指定数量的空格的 `fillblank` 操控器：

## <a name="example"></a>示例

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>另请参阅

[带参数的自定义操控器](../standard-library/custom-manipulators-with-arguments.md)
