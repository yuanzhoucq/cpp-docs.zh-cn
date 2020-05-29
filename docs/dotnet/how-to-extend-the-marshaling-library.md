---
title: 如何：扩展封送处理库
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: ab3b17638e07a54189803c83163db67c5ebf82a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545269"
---
# <a name="how-to-extend-the-marshaling-library"></a>如何：扩展封送处理库

本主题说明如何扩展封送处理库，以便在数据类型之间提供更多的转换。 用户可以为库当前不支持的任何数据转换扩展封送处理库。

可以通过以下两种方式之一扩展封送处理库-使用或不使用[Marshal_context 类](../dotnet/marshal-context-class.md)。 请参阅主题[中C++的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)，确定新转换是否需要上下文。

在这两种情况下，首先要创建新的封送处理转换文件。 这样做是为了保留标准封送库文件的完整性。 如果要将项目移植到另一台计算机或另一台程序员，则必须将新的封送处理文件与项目的其余部分一起复制。 通过这种方式，接收项目的用户可以接收新的转换，而不需要修改任何库文件。

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>使用不需要上下文的转换扩展封送处理库

1. 创建一个文件来存储新的封送处理函数，例如 MyMarshal。

1. 包含一个或多个封送库文件：

   - 用于基类型的 marshal。

   - marshal_windows windows 数据类型。

   - C++标准库数据类型 marshal_cppstd .h。

   - ATL 数据类型 marshal_atl。

1. 使用这些步骤末尾的代码编写转换函数。 在此代码中，TO 为要转换为的类型，FROM 是要从其转换的类型，`from` 是要转换的参数。

1. 将有关转换逻辑的注释替换为代码，以将 `from` 参数转换为的对象，以键入并返回转换后的对象。

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>使用需要上下文的转换扩展封送处理库

1. 创建文件以存储新的封送处理函数，例如 MyMarshal

1. 包含一个或多个封送库文件：

   - 用于基类型的 marshal。

   - marshal_windows windows 数据类型。

   - C++标准库数据类型 marshal_cppstd .h。

   - ATL 数据类型 marshal_atl。

1. 使用这些步骤末尾的代码编写转换函数。 在此代码中，若为，则为要转换为的类型，FROM 是要从其转换的类型，`toObject` 是要在其中存储结果的指针，`fromObject` 是要转换的参数。

1. 将有关初始化的注释替换为代码，以将 `toPtr` 初始化为适当的空值。 例如，如果是指针，则将其设置为 `NULL`。

1. 将有关转换逻辑的注释替换为代码，以将 `from` 参数转换*为*类型的对象。 此转换的对象将存储在 `toPtr`中。

1. 将有关设置 `toObject` 的注释替换为代码，将 `toObject` 设置为转换后的对象。

1. 替换有关使用代码清理本机资源的注释，以释放 `toPtr`分配的任何内存。 如果 `toPtr` 使用 `new`分配内存，请使用 `delete` 释放内存。

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

下面的示例使用不需要上下文的转换来扩展封送处理库。 在此示例中，代码将员工信息从本机数据类型转换为托管数据类型。

```cpp
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

在前面的示例中，`marshal_as` 函数将返回转换后的数据的句柄。 这样做是为了防止创建额外的数据副本。 直接返回变量会导致不必要的性能开销。

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>示例

下面的示例将托管数据类型的雇员信息转换为本机数据类型。 此转换需要封送处理上下文。

```cpp
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

## <a name="see-also"></a>另请参阅

[C++ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)
