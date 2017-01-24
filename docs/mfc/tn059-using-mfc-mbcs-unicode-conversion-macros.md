---
title: "TN059：使用 MFC MBCS/Unicode 转换宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "转换宏 [C++]"
  - "转换 Unicode"
  - "宏 [C++], MBCS 转换宏"
  - "MBCS [C++], 转换宏"
  - "MFCANS32.DLL"
  - "TN059"
  - "Unicode [C++], 转换宏"
  - "Unicode [C++], OLE 接口"
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN059：使用 MFC MBCS/Unicode 转换宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明如何为 MBCS\/Unicode 转换使用宏，在 AFXPRIV.H. 定义。  这些宏是最有用，如果应用程序直接与 OLE API 或由于某种原因，通常需要转换。Unicode 和 MBCS。  
  
## 概述  
 在 MFC 中，特定用于 3.x DLL \(MF CANS32 .DLL\) 自动转换。Unicode 和 MBCS 之间，当 OLE 接口名为。  此 DLL 允许是 OLE 应用程序编写的几乎透明层，则 API 和 OLE 接口，MBCS，但它们始终是 Unicode \(在 Macintosh\)。  将此层是方便以及允许的应用程序快速从 Win16 移植到 Win32 \(MFC、Microsoft Word、Microsoft Excel 和 VBA，是使用此技术\) 的某些 Microsoft 应用程序时，其一有时重要的性能造成的影响。  为此，MFC 4.x 不使用此 DLL 以及直接与 Unicode OLE 接口不可用。  为此，MFC 需要转换为 Unicode 到 MBCS，当调用一个 OLE 接口且经常时需要转换为 Unicode 的 MBCS，当 OLE 接口实现时。  若要处理这有效且轻松，很多此转换使宏创建更为容易。  
  
 创建一个这样一组最大的障碍宏是内存分配。  由于字符串不能转换的就地，必须留有保持转换的结果的新内存。  可以通过使用类似于以下所示的代码：  
  
```  
// we want to convert an MBCS string in lpszA  
int nLen = MultiByteToWideChar(CP_ACP, 0,lpszA, -1, NULL, NULL);  
LPWSTR lpszW = new WCHAR[nLen];  
MultiByteToWideChar(CP_ACP, 0,   
   lpszA, -1, lpszW, nLen);  
// use it to call OLE here  
pI->SomeFunctionThatNeedsUnicode(lpszW);  
// free the string  
delete[] lpszW;  
```  
  
 用作许多问题的此方法。  主要问题是它的调试的代码编写，测试。  是一个简单的函数调用的内容，现在更复杂。  此外，此类使具有大量运行时系统开销。  每次转换完成，堆内存在必须分配和释放。  最后，以上代码将需要为不要求此转换发生\) 的 Unicode 和 Macintosh 版本中添加适当的 \( `#ifdefs`。  
  
 我们以的解决方案中创建各掩码 1\) 平台之间的差异\) 和 2 使用一个高效的内存分配方案和 3\) 对于容易插入现有源代码的某些宏。  这是一个示例定义之一：  
  
```  
#define A2W(lpa) (\  
    ((LPCSTR)lpa == NULL) ? NULL : (\  
          _convert = (strnlen(lpa)+1),\  
        AfxA2WHelper((LPWSTR) alloca(_convert*2),   
      lpa, _convert)\  
    )\  
)  
```  
  
 使用而不是以上代码的此宏和内容为更简单：  
  
```  
// use it to call OLE here  
USES_CONVERSION;  
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));  
```  
  
 具有转换所需的额外调用，但是，使用宏简单而有效。  
  
 每个宏的实现使用 \_alloca\(\) 函数从堆栈分配内存而不是。堆  从堆栈中分配内存要比分配堆上的内存更快，并且，内存将自动释放，该函数退出时。  此外，宏避免调用 **MultiByteToWideChar** \(或 **WideCharToMultiByte**\) 超过一次。  这通过分配更多一点的内存比需要完成的。  我们知道 MBC 将转换为最多一个 **WCHAR**，用于各 **WCHAR** 我们最多具有两 MBC 字节。  通过指派有多于必要，但足以始终处理转换第二次调用第二次调用避免转换函数。  为帮助程序函数调用 **AfxA2Whelper** 收缩推送参数的数量必须完成才能执行转换 \(这导致较小的代码，而且比，则直接调用 **MultiByteToWideChar** \)。  
  
 若要为包含的宏中的空间存储临时长度，声明局部变量在每调用执行此函数使用宏转换的\_convert 是必需的。  这是调用 **USES\_CONVERSION** 宏。完成上所见示例中。  
  
 具有两个泛翻译宏和 OLE 特定宏。  这两个不同的原因设置如下所述。  任何宏位于 AFXPRIV.H。  
  
## 泛翻译宏  
 泛翻译宏窗体基础机制。  在前面的部分以及实现显示的宏示例，A2W，是一个这样“常规”宏。  它专门与 OLE。  常规组宏所示：  
  
```  
A2CW      (LPCSTR) -> (LPCWSTR)  
A2W      (LPCSTR) -> (LPWSTR)  
W2CA      (LPCWSTR) -> (LPCSTR)  
W2A      (LPCWSTR) -> (LPSTR)  
```  
  
 除执行文本转换外，还具有宏，并且帮助器用于转换 `TEXTMETRIC`、`DEVMODE`、`BSTR`与 OLE 分配的字符串函数。  这些宏已超出本讨论的范围之外。请参见 AFXPRIV.H 这些宏有关的更多信息。  
  
## OLE 转换宏  
 OLE 转换宏来处理需要 **OLESTR** 字符的函数而专门设计。  如果检查 OLE 标题，您将看到对 **LPCOLESTR** 和 **OLECHAR**的引用太多。  这些类型在非特定于平台的方法来引用在 OLE 接口的字符类型。  对在 Win16 Macintosh 平台和 **WCHAR** 的 `char` 和**OLECHAR** 映射在 Win32。  
  
 要使 **\#ifdef** 指令的个数。MFC 代码到最低有位置 OLE 字符串是包含的每个经过转换的相似宏。  下列宏最常使用：  
  
```  
T2COLE   (LPCTSTR) -> (LPCOLESTR)  
T2OLE   (LPCTSTR) -> (LPOLESTR)  
OLE2CT   (LPCOLESTR) -> (LPCTSTR)  
OLE2T   (LPCOLESTR) -> (LPCSTR)  
```  
  
 再次，则执行 `TEXTMETRIC`、`DEVMODE`、`BSTR`与 OLE 分配的字符串一样的宏。  参考 AFXPRIV.H 已获得更多信息。  
  
## 其他注意事项  
 请勿使用宏在紧凑循环。  例如，不要编写以下代码：  
  
```  
void BadIterateCode(LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   for (int ii = 0; ii < 10000; ii++)  
      pI->SomeMethod(ii, T2COLE(lpsz));  
}  
```  
  
 上面的代码可能导致堆栈上分配 MB 的内存根据字符串 `lpsz` 的内容为！  还需要时间转换循环的每个迭代的字符串。  另外，请将这种常量转换从外部循环：  
  
```  
void MuchBetterIterateCode(LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   LPCOLESTR lpszT = T2COLE(lpsz);  
   for (int ii = 0; ii < 10000; ii++)  
      pI->SomeMethod(ii, lpszT);  
}  
```  
  
 如果字符串不是一成不变的，然后封装方法调用函数。  这将允许将缓冲区都已释放。  例如：  
  
```  
void CallSomeMethod(int ii, LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   pI->SomeMethod(ii, T2COLE(lpsz));  
}  
  
void MuchBetterIterateCode2(LPCTSTR* lpszArray)  
{  
   for (int ii = 0; ii < 10000; ii++)  
      CallSomeMethod(ii, lpszArray[ii]);  
}  
```  
  
 除非返回值。方法返回之前，这意味着数据副本不返回结果的一个宏。  例如，以下代码是不好的：  
  
```  
LPTSTR BadConvert(ISomeInterface* pI)  
{  
   USES_CONVERSION;  
   LPOLESTR lpsz = NULL;  
   pI->GetFileName(&lpsz);  
   LPTSTR lpszT = OLE2T(lpsz);  
   CoMemFree(lpsz);  
   return lpszT; // bad! returning alloca memory  
}  
```  
  
 以上代码可以通过更改为复制值的内容的返回值进行修复：  
  
```  
CString BetterConvert(ISomeInterface* pI)  
{  
   USES_CONVERSION;  
   LPOLESTR lpsz = NULL;  
   pI->GetFileName(&lpsz);  
   LPTSTR lpszT = OLE2T(lpsz);  
   CoMemFree(lpsz);  
   return lpszT; // CString makes copy  
}  
```  
  
 宏是轻松轻松插入代码，但是，当上述警告，可以调用，需要小心，在使用它们。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)