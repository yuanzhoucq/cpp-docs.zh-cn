---
title: mbsinit
ms.date: 11/04/2016
api_name:
- mbsinit
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsinit
helpviewer_keywords:
- mbsinit function
ms.assetid: 4618555b-baaa-4d04-93fa-36abae411034
ms.openlocfilehash: e3b1eecc252a2bee83997aa6f2f6f47a96d3321a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952369"
---
# <a name="mbsinit"></a>mbsinit

跟踪多字节字符转换的状态。

## <a name="syntax"></a>语法

```C
int mbsinit(
   const mbstate_t* ps
);
```

### <a name="parameters"></a>参数

*ps*<br/>
指向 [mbstate_t](../../c-runtime-library/standard-types.md) 变量的指针。

## <a name="return-value"></a>返回值

如果*ps*为 NULL 或者不在转换的中间，则为非零**值**。

## <a name="remarks"></a>备注

使用采用**mbstate_t**指针的 ANSI 函数之一时，传递**mbstate_t**的地址将返回有关缓冲区中的最后一个字节是否已转换的信息。

需要安装适当的代码页来支持多字节字符。

## <a name="example"></a>示例

```cpp
// crt_mbsinit.cpp
#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <cwchar>
#include <xlocinfo.h>

#define   BUF_SIZE   0x40

wchar_t      g_wcBuf[BUF_SIZE] = L"This a wc buffer that will be over written...";
char      g_mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
int      g_nInit = strlen(g_mbBuf);

int MbsinitSample(char* szIn, wchar_t* wcOut, int nMax)
{
   mbstate_t   state = {0};
   size_t      nConvResult, nmbLen = 0, nwcLen = 0;
   wchar_t*   wcCur = wcOut;
   wchar_t*   wcEnd = wcCur + nMax;
   const char*   mbCur = szIn;
   const char*   mbEnd = mbCur + strlen(mbCur) + 1;
   char*      szLocal = setlocale(LC_ALL, "japanese");

   printf("Locale set to: \"%s\"\n", szLocal);

   if   (_setmbcp(_MB_CP_LOCALE) != -1)
   {
      while   ((mbCur < mbEnd) && (wcCur < wcEnd))
      {
         nConvResult = mbrtowc(wcCur, mbCur, 1, &state);

         switch   (nConvResult)
         {
            case 0:
            {   // done
               printf("Conversion succeeded!\nMB String: ");
               printf(szIn);
               printf("\nWC String: ");
               wprintf(wcOut);
               printf("\n");
               mbCur = mbEnd;
               break;
            }

            case -1:
            {   // encoding error
               printf("ERROR: The call to mbrtowc has detected an encoding error.\n");
               mbCur = mbEnd;
               break;
            }

            case -2:
            {   // incomplete character
               if   (!mbsinit(&state))
               {
                  printf("Currently in middle of mb conversion, state = %x\n", state);
                  // state will contain data regarding lead byte of mb character
               }

               ++nmbLen;
               ++mbCur;
               break;
            }

            default:
            {
               if   (nConvResult > 2)   // Microsoft mb should never be larger than 2
                  printf("ERROR: nConvResult = %d\n", nConvResult);

               ++nmbLen;
               ++nwcLen;
               ++wcCur;
               ++mbCur;
               break;
            }
         }
      }
   }
   else
      printf("ERROR: _setmbcp(932) failed!");

   return 0;
}

int main(int argc, char* argv[])
{
   return MbsinitSample(g_mbBuf, g_wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>示例输出

```Output
Locale set to: "Japanese_Japan.932"
Currently in middle of mb conversion, state = 9a
Currently in middle of mb conversion, state = e0
Currently in middle of mb conversion, state = f0
Conversion succeeded!
MB String: AaBbCcxXyYzZ
WC String: AaBbCcxXyYzZ
```

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
