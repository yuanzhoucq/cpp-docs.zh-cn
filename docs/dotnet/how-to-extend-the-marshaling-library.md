---
title: 如何： 扩展封送处理库 |Microsoft 文档
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
ms.openlocfilehash: 6f6503cbb0006c0c8b2e1ed113a798a23ac2ff55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135877"
---
# <a name="how-to-extend-the-marshaling-library"></a>如何：扩展封送处理库
本主题说明如何扩展封送处理库，从而提供更多数据类型之间转换。 用户可以扩展当前不支持库的任何数据转换的封送处理库。  
  
 你可以扩展中两种方式的使用或不之一的封送处理库[marshal_context 类](../dotnet/marshal-context-class.md)。 查看[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)主题，以确定新转换是否需要上下文。  
  
 在这两种情况下，您首先创建新的封送处理转换的文件。 这样做是为了保持标准封送处理库文件的完整性。 如果你想要移植到另一台计算机或另一个程序员的项目，你必须将复制与项目的其余部分一起新的封送处理文件。 这种方式，用户将获得项目会保证接收的新转换，并将不需要进行修改的任何库文件。  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>若要扩展封送处理库不需要上下文的转换  
  
1.  创建一个文件来存储新的封送处理功能，例如，MyMarshal.h。  
  
2.  包括一个或多个封送库文件：  
  
    -   marshal.h 个基类型。  
  
    -   windows 数据类型的 marshal_windows.h。  
  
    -   对于 c + + 标准库数据类型的 marshal_cppstd.h。  
  
    -   marshal_atl.h ATL 数据类型。  
  
3.  在这些步骤的末尾使用代码编写的转换函数。 在此代码中，是要将转换为的类型，FROM 是要从，转换的类型和`from`是要转换的参数。  
  
4.  将关于转换逻辑的注释替换为要转换的代码`from`到收件人的对象的参数类型和返回被转换的对象。  
  
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
  
1.  创建一个文件来存储新的封送处理功能，例如，MyMarshal.h  
  
2.  包括一个或多个封送库文件：  
  
    -   marshal.h 个基类型。  
  
    -   windows 数据类型的 marshal_windows.h。  
  
    -   对于 c + + 标准库数据类型的 marshal_cppstd.h。  
  
    -   marshal_atl.h ATL 数据类型。  
  
3.  在这些步骤的末尾使用代码编写的转换函数。 在此代码中，是要将转换为的类型，FROM 是要从，转换的类型`toObject`是要在其中存储结果，指针和`fromObject`是要转换的参数。  
  
4.  将有关正在使用代码以初始化初始化注释`toPtr`为适当的空值。 例如，如果它是一个指针，将其设置为`NULL`。  
  
5.  将关于转换逻辑的注释替换为要转换的代码`from`参数转换的对象*收件人*类型。 此转换后的对象将存储在`toPtr`。  
  
6.  将有关设置注释`toObject`替换为用于设置代码`toObject`对你已转换的对象。  
  
7.  替换关于清理代码以释放分配任何内存使用的本机资源的注释`toPtr`。 如果`toPtr`通过使用分配的内存`new`，使用`delete`可释放的内存。  
  
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
 下面的示例扩展的封送处理库不需要上下文的转换。 在此示例中，代码将转换的员工信息从本机数据类型为托管的数据类型。  
  
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
  
 在前面的示例中，`marshal_as`函数返回转换的数据的句柄。 这样做是为了防止创建数据的额外副本。 直接返回该变量将具有不必要的性能成本与之关联。  
  
```Output  
Managed name: Jeff Smith  
Managed address: 123 Main Street  
Managed zip code: 98111  
```  
  
## <a name="example"></a>示例  
 下面的示例将员工信息从托管的数据类型转换为本机数据类型。 此转换需要封送处理的上下文。  
  
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