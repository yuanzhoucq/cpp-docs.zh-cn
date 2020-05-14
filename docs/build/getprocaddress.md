---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493252"
---
# <a name="getprocaddress"></a>GetProcAddress

显式链接到 DLL 的进程会调用 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)，以获取 DLL 中导出函数的地址。 可使用返回的函数指针调用 DLL 函数。 GetProcAddress  采用 DLL 模块句柄（由 LoadLibrary  、`AfxLoadLibrary` 或 GetModuleHandle  返回）作为参数，并采用要调用的函数的名称或函数的导出序号。

因为通过指针调用 DLL 函数，并且没有编译时类型检查，所以请确保函数的参数正确，以便不会超过在堆栈上分配的内存以及导致访问冲突。 帮助提供类型安全的一种方法是查看导出函数的函数原型，并为函数指针创建匹配的 typedef。 例如：

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

如何指定调用 GetProcAddress  时所需的函数取决于 DLL 的生成方式。

仅当要链接到的 DLL 使用模块定义 (.def) 文件生成，并且序号随函数在 DLL .def 文件的 EXPORTS  节中列出时，才能获取导出序号。 如果 DLL 具有许多导出函数，则与使用函数名称相比，使用导出序号调用 GetProcAddress  会稍微快一些，因为导出序号充当 DLL 导出表中的索引。 使用导出序号，GetProcAddress  可以直接查找函数，而不是将指定名称与 DLL 导出表中的函数名进行比较。 但是，仅当可控制将序号分配给 .def 文件中的导出函数时，才应使用导出序号调用 GetProcAddress  。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [使用 DEF 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
