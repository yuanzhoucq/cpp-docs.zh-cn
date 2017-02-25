---
title: "如何：扩展封送处理库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "封送处理库, 扩展"
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：扩展封送处理库
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题说明如何扩展封送处理库，从而在数据类型之间提供更多转换。  用户可以为库当前不支持的任何数据转换扩展封送处理库。  
  
 可以通过两种方式之一扩展封送处理库 — 既可以使用也可以不使用 [marshal\_context 类](../dotnet/marshal-context-class.md)。  请查看 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)主题，确定新转换是否需要上下文。  
  
 在这两种情况下，首先需要为新封送处理转换创建一个文件。  这样做是为了保留标准封送处理库文件的完整性。  如果需要将一个项目导入到另一台计算机或转到另一程序员，则必须将新的封送处理文件与项目的其余部分一起复制。  通过这种方式，可以保证接收项目的用户接收新转换，并且不必修改任何库文件。  
  
### 使用不需要上下文的转换扩展封送处理库  
  
1.  创建一个文件来存储新的封送处理函数，例如，MyMarshal.h。  
  
2.  包括以下一个或多个封送库文件：  
  
    -   用于基类型的 marshal.h。  
  
    -   用于 Windows 数据类型的 marshal\_windows.h。  
  
    -   用于 STL 数据类型的 marshal\_cppstd.h。  
  
    -   用于 ATL 数据类型的 marshal\_atl.h。  
  
3.  使用这些步骤末尾的代码编写转换函数。  在此代码中，TO 是要转换到的类型，FROM 是要从中转换的类型，`from` 是要转换的参数。  
  
4.  使用代码替换关于转换逻辑的注释，将 `from` 参数转换为 TO 类型的一个对象，并返回被转换的对象。  
  
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
  
### 使用需要上下文的转换扩展封送处理库  
  
1.  创建一个文件来存储新的封送处理函数，例如，MyMarshal.h  
  
2.  包括以下一个或多个封送库文件：  
  
    -   用于基类型的 marshal.h。  
  
    -   用于 Windows 数据类型的 marshal\_windows.h。  
  
    -   用于 STL 数据类型的 marshal\_cppstd.h。  
  
    -   用于 ATL 数据类型的 marshal\_atl.h。  
  
3.  使用这些步骤末尾的代码编写转换函数。  在此代码中，TO 是要转换到的类型，FROM 是要从中转换的类型，`toObject` 是存储结果的指针，`fromObject` 是要转换的参数。  
  
4.  使用代码替换关于初始化的注释，将 `toPtr` 初始化为适当的空值。  例如，如果是指针，则将其设置为 `NULL`。  
  
5.  使用将 `from` 参数转换为 *TO* 类型的一个对象代码替换关于转换逻辑的注释。  此被转换的对象将存储在 `toPtr` 中。  
  
6.  使用代码替换关于设置 `toObject` 的注释，将 `toObject` 设置为被转换的对象。  
  
7.  使用代码替换关于清理本机资源的注释，以释放由 `toPtr` 分配的任何内存。  如果 `toPtr` 使用 `new` 分配了内存，请使用 `delete` 释放内存。  
  
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
  
## 示例  
 以下示例将使用不需要上下文的转换来扩展封送处理库。  在此示例中，代码将员工信息从本机数据类型转换为托管数据类型。  
  
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
  
 在上一示例中，`marshal_as` 函数返回被转换数据的句柄。  这样做是为了防止创建数据的另一个副本。  直接返回变量将产生与之相关的不必要的性能开销。  
  
  **Managed name: Jeff Smith**  
**Managed address: 123 Main Street**  
**Managed zip code: 98111**   
## 示例  
 下面的示例将员工信息从托管数据类型转换为本机数据类型。  此转换需要封送处理上下文。  
  
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
  
  **Native name: Jeff Smith**  
**Native address: 123 Main Street**  
**Native zip code: 98111**   
## 请参阅  
 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)