---
title: collection_adapter::collection_adapter (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
dev_langs:
- C++
helpviewer_keywords:
- collection_adapter member [STL/CLR]
ms.assetid: 7e2bb75b-d735-4135-9523-719683e06fe9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ddb802e372dfb10acdc6280622bf1ed59a422987
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108957"
---
# <a name="collectionadaptercollectionadapter-stlclr"></a>collection_adapter::collection_adapter (STL/CLR)
将构造一个适配器对象。  
  
## <a name="syntax"></a>语法  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>参数  
 集合  
 要包装的 BCL 句柄。  
  
 右  
 要复制的对象。  
  
## <a name="remarks"></a>备注  
 构造函数：  
  
 `collection_adapter();`  
  
 初始化与存储的句柄`nullptr`。  
  
 构造函数：  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 初始化与存储的句柄`right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`。  
  
 构造函数：  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 初始化与存储的句柄`right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`。  
  
 构造函数：  
  
 `collection_adapter(Coll^ collection);`  
  
 初始化存储与句柄与`collection`。  
  
## <a name="example"></a>示例  
  
```  
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/适配器 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::operator= (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)