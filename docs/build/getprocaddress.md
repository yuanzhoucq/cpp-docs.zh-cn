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
ms.openlocfilehash: 5ee985da29e38bfb262c72315a57c0b588b2e82e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810167"
---
# <a name="getprocaddress"></a>GetProcAddress

显式链接到 DLL 调用的进程[GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)获取 DLL 中导出函数的地址。 使用返回的函数指针调用 DLL 函数。 **GetProcAddress** DLL 模块句柄将作为参数 (通过以下任一方法返回**LoadLibrary**， `AfxLoadLibrary`，或**GetModuleHandle**) 和采用的所需的函数名称到调用或函数的导出序号。

因为调用 DLL 函数通过指针并且没有任何编译时类型检查，请确保函数的参数正确，以便不超出在堆栈上分配的内存，并导致访问冲突。 帮助提供类型安全的一种方法是查看导出的函数的函数原型，并创建函数指针的匹配 typedef。 例如：

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

如何指定所需时调用的函数**GetProcAddress**取决于 DLL 的生成。

如果要链接到 DLL 生成与模块定义 (.def) 文件，并列出中的函数的序号，仅可以获取导出序号**导出**DLL 的.def 文件的部分。 调用**GetProcAddress**与导出序号，而不是函数名称，会稍微快一点如果 DLL 具有许多导出的函数，因为导出序号用作索引到 DLL 的导出表。 使用导出序号**GetProcAddress**可以找到而比较指定的名称与 DLL 的导出表中的函数名称不是直接函数。 但是，应调用**GetProcAddress**使用导出序号仅当你可以控制的序号分配到.def 文件中导出的函数。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)

- [使用 DEF 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
