---
title: 如何： 扩展封送处理库 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4e50ca6fd99f373a65ba0592114cb7d9eedb242
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384892"
---
# <a name="how-to-extend-the-marshaling-library"></a>如何：扩展封送处理库

本主题说明如何扩展封送处理库，以提供更多数据类型之间转换。 用户可以扩展目前不支持库的任何数据转换的封送处理库。

您可以扩展的封送处理库中有两种-带或不带[marshal_context 类](../dotnet/marshal-context-class.md)。 审阅[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)主题，以确定新转换是否需要上下文。

在这两种情况下，首先创建新的封送处理转换的文件。 这样做是为了保持标准封送处理库文件的完整性。 如果你想要移植到另一台计算机或另一个程序员的项目，则必须复制项目的其余部分以及新的封送处理文件。 在这种方式，接收项目的用户将保证能够收到新的转换，并将无需修改任何库文件。

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>若要扩展封送处理库不需要上下文的转换

1. 创建一个文件来存储新的封送处理函数，例如，MyMarshal.h。

1. 包括一个或多封送库文件：

   - marshal.h 对基类型。

   - windows 数据类型为 marshal_windows.h。

   - marshal_cppstd.h 适用于 c + + 标准库的数据类型。

   - marshal_atl.h ATL 数据类型。

1. 使用以下步骤结束时代码编写的转换函数。 在此代码中，是要将转换为的类型，FROM 是要从中转换的类型和`from`是要转换的参数。

1. 使用转换的代码替换关于转换逻辑的注释`from`参数转换到的对象类型和返回的已转换的对象。

```
namespace msclr {
   namespace interop {
      template<>
      inline TO marshal_as<TO, FROM> (const FROM& from) {
         // Insert conversion logic here, and return a TO parameter.
      }
   }
}
```

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>若要扩展封送处理库需要上下文的转换

1. 创建一个文件来存储新的封送处理函数，例如，MyMarshal.h

1. 包括一个或多封送库文件：

   - marshal.h 对基类型。

   - windows 数据类型为 marshal_windows.h。

   - marshal_cppstd.h 适用于 c + + 标准库的数据类型。

   - marshal_atl.h ATL 数据类型。

1. 使用以下步骤结束时代码编写的转换函数。 在此代码中，是要将转换为的类型，FROM 是要从中转换的类型`toObject`是要在其中存储结果的指针和`fromObject`是要转换的参数。

1. 将有关初始化代码，以初始化注释为`toPtr`为适当的空值。 例如，如果它是一个指针，将其设置为`NULL`。

1. 使用转换的代码替换关于转换逻辑的注释`from`转换为对象的参数*TO*类型。 此转换后的对象将存储在`toPtr`。

1. 替换关于设置的注释`toObject`代码，以设置`toObject`到您已转换的对象。

1. 将有关清理本机资源，若要释放分配任何内存的代码注释为`toPtr`。 如果`toPtr`通过使用分配的内存`new`，使用`delete`可释放的内存。

```
namespace msclr {
   namespace interop {
      template<>
      ref class context_node<TO, FROM> : public context_node_base
      {
      private:
         TO toPtr;
      public:
         context_node(TO& toObject, FROM fromObject)
         {
            // (Step 4) Initialize toPtr to the appropriate empty value.
            // (Step 5) Insert conversion logic here.
            // (Step 6) Set toObject to the converted parameter.
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // (Step 7) Clean up native resources.
         }
      };
   }
}
```

## <a name="example"></a>示例

下面的示例扩展了具有不需要上下文的转换的封送处理库。 在此示例中，代码将转换的员工信息从本机数据类型为托管的数据类型。

```
// MyMarshalNoContext.cpp
// compile with: /clr
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   char* name;
   char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {
         ManagedEmp^ toValue = gcnew ManagedEmp;
         toValue->name = marshal_as<System::String^>(from.name);
         toValue->address = marshal_as<System::String^>(from.address);
         toValue->zipCode = from.zipCode;
         return toValue;
      }
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   NativeEmp employee;

   employee.name = "Jeff Smith";
   employee.address = "123 Main Street";
   employee.zipCode = 98111;

   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);

   Console::WriteLine("Managed name: {0}", result->name);
   Console::WriteLine("Managed address: {0}", result->address);
   Console::WriteLine("Managed zip code: {0}", result->zipCode);

   return 0;
}
```

在上一示例中，`marshal_as`函数返回的句柄转换后的数据。 这样做是为了防止创建额外的数据的副本。 直接返回该变量会有不必要的性能成本与它关联。

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>示例

下面的示例将员工信息从托管的数据类型转换为本机数据类型。 此转换需要封送处理上下文。

```
// MyMarshalContext.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   const char* name;
   const char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base
      {
      private:
         NativeEmp* toPtr;
         marshal_context context;
      public:
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)
         {
            // Conversion logic starts here
            toPtr = NULL;

            const char* nativeName;
            const char* nativeAddress;

            // Convert the name from String^ to const char*.
            System::String^ tempValue = fromObject->name;
            nativeName = context.marshal_as<const char*>(tempValue);

            // Convert the address from String^ to const char*.
            tempValue = fromObject->address;
            nativeAddress = context.marshal_as<const char*>(tempValue);

            toPtr = new NativeEmp();
            toPtr->name = nativeName;
            toPtr->address = nativeAddress;
            toPtr->zipCode = fromObject->zipCode;

            toObject = toPtr;
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // When the context is deleted, it will free the memory
            // allocated for toPtr->name and toPtr->address, so toPtr
            // is the only memory that needs to be freed.
            if (toPtr != NULL) {
               delete toPtr;
               toPtr = NULL;
            }
         }
      };
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   ManagedEmp^ employee = gcnew ManagedEmp();

   employee->name = gcnew String("Jeff Smith");
   employee->address = gcnew String("123 Main Street");
   employee->zipCode = 98111;

   marshal_context context;
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);

   if (result != NULL) {
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",
         result->name, result->address, result->zipCode);
   }

   return 0;
}
```

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>请参阅

[C++ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)