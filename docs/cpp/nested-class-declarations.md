---
title: 嵌套类声明 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fe55a1f67ff3c6ac06f1d6431e6e1a2fb8052d8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="nested-class-declarations"></a>嵌套类声明
可以在一个类的范围内声明另一个类。 这样的类称为“嵌套类”。 嵌套类被视为在封闭类的范围内且可在该范围内使用。 若要从嵌套类的即时封闭范围之外的某个范围引用该类，则必须使用完全限定名。  
  
 下面的示例演示如何声明嵌套类：  
  
```  
// nested_class_declarations.cpp  
class BufferedIO  
{  
public:  
   enum IOError { None, Access, General };  
  
   // Declare nested class BufferedInput.  
   class BufferedInput  
   {  
   public:  
      int read();  
      int good()  
      {  
         return _inputerror == None;  
      }  
   private:  
       IOError _inputerror;  
   };  
  
   // Declare nested class BufferedOutput.  
   class BufferedOutput  
   {  
      // Member list  
   };  
};  
  
int main()  
{  
}  
```  
  
 在 `BufferedIO::BufferedInput` 中声明 `BufferedIO::BufferedOutput` 和 `BufferedIO`。 这些类名称在类 `BufferedIO` 的范围外不可见。 但是，`BufferedIO` 类型的对象不包含 `BufferedInput` 或 `BufferedOutput` 类型的任何对象。  
  
 嵌套类只能从封闭类中直接使用名称、类型名称，静态成员的名称和枚举数。 若要使用其他类成员的名称，您必须使用指针、引用或对象名。  
  
 在前面的 `BufferedIO` 示例中，枚举 `IOError` 可由嵌套类中的成员函数、`BufferedIO::BufferedInput` 或 `BufferedIO::BufferedOutput` 直接访问，如函数 `good` 中所示。  
  
> [!NOTE]
>  嵌套类仅在类范围内声明类型。 它们不会导致创建嵌套类的包含对象。 前面的示例声明两个嵌套类，但未声明这些类类型的任何对象。  
  
 在将类型名称与前向声明一起声明时，会引发嵌套类声明的范围可见性的异常。  在这种情况下，由前向声明声明的类名在封闭类的外部可见，其范围定义为最小的封闭非类范围。  例如：  
  
```  
// nested_class_declarations_2.cpp  
class C  
{  
public:  
    typedef class U u_t; // class U visible outside class C scope  
    typedef class V {} v_t; // class V not visible outside class C  
};  
  
int main()  
{  
    // okay, forward declaration used above so file scope is used  
    U* pu;  
  
    // error, type name only exists in class C scope  
    u_t* pu2; // C2065  
  
    // error, class defined above so class C scope  
    V* pv; // C2065  
  
    // okay, fully qualified name  
    C::V* pv2;  
}  
```  
  
## <a name="access-privilege-in-nested-classes"></a>嵌套类中的访问权限  
 将一个类嵌入另一个类中不会为嵌入类的成员函数提供特殊访问权限。 同样，封闭类的成员函数不具有对嵌套类的成员的特殊访问权限。  
  
## <a name="member-functions-in-nested-classes"></a>嵌套类中的成员函数  
 在嵌套类中声明的成员函数可在文件范围中定义。 前面的示例可能已编写：  
  
```  
// member_functions_in_nested_classes.cpp  
class BufferedIO  
{  
public:  
    enum IOError { None, Access, General };  
    class BufferedInput  
    {  
    public:  
        int read(); // Declare but do not define member  
        int good(); //  functions read and good.  
    private:  
        IOError _inputerror;  
    };  
  
    class BufferedOutput  
    {  
        // Member list.  
    };  
};  
// Define member functions read and good in  
//  file scope.  
int BufferedIO::BufferedInput::read()  
{  
   return(1);  
}  
  
int BufferedIO::BufferedInput::good()  
{  
    return _inputerror == None;  
}  
int main()  
{  
}  
```  
  
 在前面的示例中，*限定类型名称*语法用于声明函数名称。 声明：  
  
```  
BufferedIO::BufferedInput::read()  
```  
  
 表示“作为 `read` 类（位于 `BufferedInput` 类的范围中）的成员的 `BufferedIO` 函数。” 因为此声明使用*限定类型名称*语法，还可能有以下形式的构造：  
  
```  
typedef BufferedIO::BufferedInput BIO_INPUT;  
  
int BIO_INPUT::read()  
```  
  
 上述声明与前一个声明等效，但它使用了 `typedef` 名称来代替类名称。  
  
## <a name="friend-functions-in-nested-classes"></a>嵌套类中的友元函数  
 嵌套类中声明的友元函数被认为是在嵌套类而不是封闭类的范围内。 因此，友元函数未获得对封闭类的成员或成员函数的特定访问权限。 如果需要使用在友元函数中的嵌套类中声明的名称，并且友元函数是在文件范围内定义的，请使用限定的类型名称，如下所示：  
  
```  
// friend_functions_and_nested_classes.cpp  
  
#include <string.h>  
  
enum  
{  
    sizeOfMessage = 255  
};  
  
char *rgszMessage[sizeOfMessage];  
  
class BufferedIO  
{  
public:  
    class BufferedInput  
    {  
    public:  
        friend int GetExtendedErrorStatus();  
        static char *message;  
        static int  messageSize;  
        int iMsgNo;  
   };  
};  
  
char *BufferedIO::BufferedInput::message;  
int BufferedIO::BufferedInput::messageSize;  
  
int GetExtendedErrorStatus()  
{  
    int iMsgNo = 1; // assign arbitrary value as message number  
  
    strcpy_s( BufferedIO::BufferedInput::message,  
              BufferedIO::BufferedInput::messageSize,  
              rgszMessage[iMsgNo] );  
  
    return iMsgNo;  
}  
  
int main()  
{  
}  
```  
  
 以下代码演示声明为友元函数的函数 `GetExtendedErrorStatus`。 在文件范围内定义的函数中，将消息从静态数组复制到类成员中。 请注意，`GetExtendedErrorStatus` 的更佳实现是将其声明为：  
  
```  
int GetExtendedErrorStatus( char *message )  
```  
  
 利用前面的接口，许多类可以通过传递要复制错误消息的内存位置来使用此函数的服务。  
  
## <a name="see-also"></a>请参阅  
 [类和结构](../cpp/classes-and-structs-cpp.md)