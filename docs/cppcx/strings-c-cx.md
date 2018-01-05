---
title: "字符串 (C + + /cli CX) |Microsoft 文档"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
caps.latest.revision: "22"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 66a08038825b2ca76a8d18e5103b5569feb51cb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strings-ccx"></a>字符串 (C++/CX)
Windows 运行时中的文本表示在 C + + /cli CX 通过[platform:: string 类](../cppcx/platform-string-class.md)。 使用`Platform::String Class`时将字符串传递来回方法在 Windows 运行时类中，或与其他 Windows 运行时组件跨应用程序二进制接口 (ABI) 边界的进行交互时。 虽然 `Platform::String Class` 为几种常见字符串操作提供方法，但它还不是全功能字符串类。 在您的 C++ 模块中，将标准 C++ 字符串类型（如 [wstring](../standard-library/basic-string-class.md) ）用于任何大量的文本处理，然后将最终结果转换为 [Platform::String^](../cppcx/platform-string-class.md) ，最后再向（或从）公共接口传递它。 在 `wstring` 或 `wchar_t*` 与 `Platform::String`之间进行转换很容易也很有效。  
  
 **快速传递**  
  
 在某些情况下，编译器可以验证它能否安全地构造 `Platform::String` 或将 `String` 传递到一个函数而无需复制基础字符串数据。 此类操作称为 *快速传递* ，它们以透明方式发生。  
  
## <a name="string-construction"></a>字符串构造  
 `String` 对象的值是 `char16` （16 位 Unicode）字符的不可变（只读）序列。 由于 `String` 对象是不可变的，因此将新字符串文本分配给 `String` 变量其实就是用新的 `String` 对象替换原始 `String` 对象。 串联运算涉及析构原始 `String` 对象和创建新对象。  
  
 **文本**  
  
 一个 *文本字符* 就是用单引号括起来的一个字符，一个 *文本字符串* 就是用双引号括起来的一个字符序列。 如果使用文本初始化 String^ 变量，则编译器假定文本由 `char16` 字符组成。 也就是说，在 **_T()** 或 **TEXT()** 宏中，不必在文本前加上字符串修饰符“L”或用引号将文本括起来。 有关 Unicode 的 C++ 支持的更多信息，请参见 [Unicode Programming Summary](../text/unicode-programming-summary.md)。  
  
 下面的示例演示用来构造 `String` 对象的各种方法。  
  
 [!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]  
  
## <a name="string-handling-operations"></a>字符串处理操作  
 `String` 类为连接、比较字符串和其他基本字符串操作提供方法和运算符。 若要执行更广泛的字符串操作，请使用 `String::Data()` 成员函数来检索 `String^` 对象的值作为 `const wchar_t*`。 然后使用该值初始化 `std::wstring`，后者提供丰富的字符串处理函数。  
  
 [!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]  
  
## <a name="string-conversions"></a>字符串转换  
 `Platform::String` 中只能包含 `char16` 字符或 `NULL` 字符。 如果你的应用程序必须使用 8 位字符，则使用[string:: data](../cppcx/platform-string-class.md#data)提取文本作为`const wchar_t*`。 然后，您可以使用适当的 Windows 函数或标准库函数对数据进行操作并将其转换回 `wchar_t*` 或 [wstring](../standard-library/basic-string-class.md)（用于构造新的 `Platform::String`表示。  
  
 下面的代码片段演示 `String^` 变量和 `wstring` 变量间如何相互转换。 有关此示例中使用的字符串操作的更多信息，请参见 [basic_string::replace](../standard-library/basic-string-class.md#replace)。  
  
 [!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]  
  
## <a name="string-length-and-embedded-null-values"></a>字符串长度和嵌入的 NULL 值  
 [String:: length](../cppcx/platform-string-class.md#length)返回字符串，不的字节数中的字符数。 当使用堆栈语义构造字符串时，一般不计算终止 NULL 字符，除非您明确指定。  
  
 `Platform::String` 可以包含嵌入的 NULL 值，但前提是 NULL 必须为串联运算的结果。 字符串文本中不支持嵌入的 NULL，因此，不能以这种方式使用嵌入的 NULL 初始化 `Platform::String`。 在显示该字符串时（例如，将字符串分配给 `Platform::String` 属性时），将忽略 `TextBlock::Text` 中嵌入的 NULL 值。 当字符串值由 `Data` 属性返回时，将删除嵌入的 NULL。  
  
## <a name="stringreference"></a>StringReference  
 在某些情况下代码 (a) 接收 std:: wstring、 wchar_t 字符串或 L""字符串文本，并直接将其传递到另一个方法采用 String ^ 作为输入参数。 只要原始字符串缓冲区本身在函数返回之前保持有效且不发生变化，则可以将 `wchar_t*` 字符串或字符串文本转换为 [Platform::StringReference](../cppcx/platform-stringreference-class.md)，然后将其代替 `Platform::String^`传入。 之所以允许这样做，是因为 `StringReference` 具有用户定义的到 `Platform::String^`的转换。 通过使用 `StringReference` ，可避免创建字符串数据的额外副本。 在传递大量字符串的循环中或传递非常大的字符串时，可通过使用 `StringReference`显著提高潜在性能。 但是，由于 `StringReference` 实质上是借用原始字符串缓冲区，因此必须格外小心，以免损坏内存。 不应将 `StringReference` 传递给异步方法，除非可以保证原始字符串在该方法返回时处于范围之内。 如果发生第二个记录分配操作，从 StringReference 初始化的 String^ 将强制分配和复制字符串数据。 在此情况下， `StringReference`的性能优势将丧失。  
  
 请注意， `StringReference` 是标准的 C++ 类类型，而非 ref 类，不能用于您定义的 ref 类的公共接口。  
  
 下面的示例演示如何使用 StringReference：  
  
```  
void GetDecodedStrings(std::vector<std::wstring> strings)  
{  
    using namespace Windows::Security::Cryptography;  
    using namespace Windows::Storage::Streams;  
  
    for (auto&& s : strings)  
    {  
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)  
        // Call using StringReference:  
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));  
  
        //...do something with buffer  
    }  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [内置类型](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)