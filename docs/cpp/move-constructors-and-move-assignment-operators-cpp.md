---
title: "移动构造函数和移动赋值运算符 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- move constructor
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 07debd120c7757c049d1e3d23dfe1bb065a3cc17
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="move-constructors-and-move-assignment-operators-c"></a>移动构造函数和移动赋值运算符 (C++)
本主题介绍如何编写*移动构造函数*和移动赋值运算符的 c + + 类。 利用移动构造函数，您可以实现移动语义，从而显著提高应用程序的性能。 有关移动语义的详细信息，请参阅[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 此主题基于用于管理内存缓冲区的 C++ 类 `MemoryBlock`。  
  
```cpp  
// MemoryBlock.h  
#pragma once  
#include <iostream>  
#include <algorithm>  
  
class MemoryBlock  
{  
public:  
  
   // Simple constructor that initializes the resource.  
   explicit MemoryBlock(size_t length)  
      : _length(length)  
      , _data(new int[length])  
   {  
      std::cout << "In MemoryBlock(size_t). length = "  
                << _length << "." << std::endl;  
   }  
  
   // Destructor.  
   ~MemoryBlock()  
   {  
      std::cout << "In ~MemoryBlock(). length = "  
                << _length << ".";  
  
      if (_data != nullptr)  
      {  
         std::cout << " Deleting resource.";  
         // Delete the resource.  
         delete[] _data;  
      }  
  
      std::cout << std::endl;  
   }  
  
   // Copy constructor.  
   MemoryBlock(const MemoryBlock& other)  
      : _length(other._length)  
      , _data(new int[other._length])  
   {  
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "   
                << other._length << ". Copying resource." << std::endl;  
  
      std::copy(other._data, other._data + _length, _data);  
   }  
  
   // Copy assignment operator.  
   MemoryBlock& operator=(const MemoryBlock& other)  
   {  
      std::cout << "In operator=(const MemoryBlock&). length = "   
                << other._length << ". Copying resource." << std::endl;  
  
      if (this != &other)  
      {  
         // Free the existing resource.  
         delete[] _data;  
  
         _length = other._length;  
         _data = new int[_length];  
         std::copy(other._data, other._data + _length, _data);  
      }  
      return *this;  
   }  
  
   // Retrieves the length of the data resource.  
   size_t Length() const  
   {  
      return _length;  
   }  
  
private:  
   size_t _length; // The length of the resource.  
   int* _data; // The resource.  
};  
```  
  
 以下过程介绍如何为示例 C++ 类编写移动构造函数和移动赋值运算符。  
  
### <a name="to-create-a-move-constructor-for-a-c-class"></a>为 C++ 创建移动构造函数  
  
1.  定义一个空的构造函数方法，该方法采用一个对类类型的右值引用作为参数，如以下示例所示：  
  
    ```cpp  
    MemoryBlock(MemoryBlock&& other)  
       : _data(nullptr)  
       , _length(0)  
    {  
    }  
    ```  
  
2.  在移动构造函数中，将源对象中的类数据成员添加到要构造的对象：  
  
    ```cpp  
    _data = other._data;  
    _length = other._length;  
    ```  
  
3.  将源对象的数据成员分配给默认值。 这可以防止析构函数多次释放资源（如内存）:  
  
    ```cpp  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>为 C++ 类创建移动赋值运算符  
  
1.  定义一个空的赋值运算符，该运算符采用一个对类类型的右值引用作为参数并返回一个对类类型的引用，如以下示例所示：  
  
    ```cpp  
    MemoryBlock& operator=(MemoryBlock&& other)  
    {  
    }  
    ```  
  
2.  在移动赋值运算符中，如果尝试将对象赋给自身，则添加不执行运算的条件语句。  
  
    ```cpp  
    if (this != &other)  
    {  
    }  
    ```  
  
3.  在条件语句中，从要将其赋值的对象中释放所有资源（如内存）。  
  
     以下示例从要将其赋值的对象中释放 `_data` 成员：  
  
    ```cpp  
    // Free the existing resource.  
    delete[] _data;  
    ```  
  
     执行第一个过程中的步骤 2 和步骤 3 以将数据成员从源对象转移到要构造的对象：  
  
    ```cpp  
    // Copy the data pointer and its length from the   
    // source object.  
    _data = other._data;  
    _length = other._length;  
  
    // Release the data pointer from the source object so that  
    // the destructor does not free the memory multiple times.  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
4.  返回对当前对象的引用，如以下示例所示：  
  
    ```cpp  
    return *this;  
    ```  
  
## <a name="example"></a>示例  
 以下示例显示了 `MemoryBlock` 类的完整移动构造函数和移动赋值运算符：  
  
```cpp  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "   
             << other._length << ". Moving resource." << std::endl;  
  
   // Copy the data pointer and its length from the   
   // source object.  
   _data = other._data;  
   _length = other._length;  
  
   // Release the data pointer from the source object so that  
   // the destructor does not free the memory multiple times.  
   other._data = nullptr;  
   other._length = 0;  
}  
  
// Move assignment operator.  
MemoryBlock& operator=(MemoryBlock&& other)  
{  
   std::cout << "In operator=(MemoryBlock&&). length = "   
             << other._length << "." << std::endl;  
  
   if (this != &other)  
   {  
      // Free the existing resource.  
      delete[] _data;  
  
      // Copy the data pointer and its length from the   
      // source object.  
      _data = other._data;  
      _length = other._length;  
  
      // Release the data pointer from the source object so that  
      // the destructor does not free the memory multiple times.  
      other._data = nullptr;  
      other._length = 0;  
   }  
   return *this;  
}  
```  
  
## <a name="example"></a>示例  
 以下示例演示移动语义如何能提高应用程序的性能。 此示例将两个元素添加到一个矢量对象，然后在两个现有元素之间插入一个新元素。 在 Visual c + + 2010 中，`vector`类使用移动语义来高效地执行插入操作，通过移动而不是将其复制向量的元素。  
  
```cpp  
// rvalue-references-move-semantics.cpp  
// compile with: /EHsc  
#include "MemoryBlock.h"  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
   // Create a vector object and add a few elements to it.  
   vector<MemoryBlock> v;  
   v.push_back(MemoryBlock(25));  
   v.push_back(MemoryBlock(75));  
  
   // Insert a new element into the second position of the vector.  
   v.insert(v.begin() + 1, MemoryBlock(50));  
}  
```  
  
 该示例产生下面的输出：  
  
```  
In MemoryBlock(size_t). length = 25.  
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(size_t). length = 75.  
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(size_t). length = 50.  
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.  
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.  
In operator=(MemoryBlock&&). length = 75.  
In operator=(MemoryBlock&&). length = 50.  
In ~MemoryBlock(). length = 0.  
In ~MemoryBlock(). length = 0.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
```  
  
 在 Visual c + + 2010 中之前, 该示例产生下面的输出：  
  
```  
In MemoryBlock(size_t). length = 25.  
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In MemoryBlock(size_t). length = 75.  
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
In MemoryBlock(size_t). length = 50.  
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.  
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.  
In operator=(const MemoryBlock&). length = 75. Copying resource.  
In operator=(const MemoryBlock&). length = 50. Copying resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
```  
  
 使用移动语义的此示例版本比不使用移动语义的版本更高效，因为前者执行的复制、内存分配和内存释放操作更少。  
  
## <a name="robust-programming"></a>可靠编程  
 若要防止资源泄漏，请始终释放移动赋值运算符中的资源（如内存、文件句柄和套接字）。  
  
 若要防止不可恢复的资源损坏，请正确处理移动赋值运算符中的自我赋值。  
  
 如果为您的类同时提供了移动构造函数和移动赋值运算符，则可以编写移动构造函数来调用移动赋值运算符，从而消除冗余代码。 以下示例显示了调用移动赋值运算符的移动构造函数的修改后的版本：  
  
```  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   *this = std::move(other);  
}  
```  
  
 [Std:: move](../standard-library/utility-functions.md#move)函数保留的右值属性`other`参数。  
  
## <a name="see-also"></a>另请参阅  
 [右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)   
 [\<实用程序 > 移动](http://msdn.microsoft.com/en-us/abef7e85-9dd6-4724-85da-d7f7fe95dca9)
