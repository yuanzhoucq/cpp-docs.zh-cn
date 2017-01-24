---
title: "浮点支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.math"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "浮点数字"
  - "浮点数字, 数学例程"
  - "数学例程"
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
caps.latest.revision: 17
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 浮点支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多 Microsoft 运行时库函数都需要数学协处理器或伴随编译器的浮点库中的浮点支持。  仅在需要时加载浮点支持函数。  
  
 当你使用对 `printf` 或 `scanf` 系列中某个函数的调用的格式字符串中的浮点类型说明符时，你必须指定浮点值或指向参数列表中的浮点值的指针，以告知编译器需要浮点支持。  
  
 有关显示如何处理浮点异常的示例代码，请参阅 [\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)。  
  
 由 [\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) 函数控制的中间值的浮点精度。  默认情况下，将 `_controlfp` 中的精度控制设置为 53 位 \(\_PC\_53\)。  使用 FP10.OBJ 进行链接会将默认精度控制更改为 64 位 \(\_PC\_64\)。  在链接器命令行上，FP10.OBJ 必须显示在 LIBC.LIB、LIBCMT.LIB 或 MSVCRT.LIB 之前。  
  
### 浮点函数  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[abs](../Topic/abs.md)|返回 `int` 的绝对值|[\<caps:sentence id\="tgt14" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[acos、acosf](../c-runtime-library/reference/acos-acosf-acosl.md)|计算反余弦|[\<caps:sentence id\="tgt17" sentenceid\="954a441495360a1fa8b0170297b2ff38" class\="tgtSentence"\>System::Math::Acos\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)|  
|[asin、asinf](../c-runtime-library/reference/asin-asinf-asinl.md)|计算反正弦|[\<caps:sentence id\="tgt20" sentenceid\="313917cde9698a0924536719f5bece25" class\="tgtSentence"\>System::Math::Asin\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.asin.aspx)|  
|[atan、atanf、atan2、atan2f](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|计算反正切|[System::Math::Atan](https://msdn.microsoft.com/en-us/library/system.math.atan.aspx)、[System::Math::Atan2](https://msdn.microsoft.com/en-us/library/system.math.atan2.aspx)|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将字符字符串转换为双精度浮点值|[System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)、[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[贝塞尔函数](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|计算贝塞尔函数 `_j0`、`_j1`、`_jn`、`_y0`、`_y1`、`_yn`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关详细信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|查找复数的绝对值|不适用。|  
|[cbrt](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|计算立方根|不适用。|  
|[ceil、ceilf](../c-runtime-library/reference/ceil-ceilf-ceill.md)|查找整数上限|[\<caps:sentence id\="tgt39" sentenceid\="656009d71fb974368bded363746de018" class\="tgtSentence"\>System::Math::Ceiling\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.ceiling.aspx)|  
|[\_chgsign、\_chgsignf、\_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|反转双精度浮点或长双精度浮点参数的符号|不适用。|  
|[\_clear87、\_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|获取和清除浮点状态字|不适用。|  
|[\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md), [\_controlfp\_s](../c-runtime-library/reference/controlfp-s.md)|获取旧的浮点控制字并设置新的控制字值|不适用。|  
|[copysign、copysignf、copysignl、\_copysign、\_copysignf、\_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|返回一个具有另一个值的符号的值|不适用。|  
|[cos、cosf、cosh、coshf](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|计算余弦|[System::Math::Cos](https://msdn.microsoft.com/en-us/library/system.math.cos.aspx)、[System::Math::Cosh](https://msdn.microsoft.com/en-us/library/system.math.cosh.aspx)|  
|[difftime](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|计算两个指定的时间值之间的差值|[\<caps:sentence id\="tgt54" sentenceid\="5f4f365a3cd7f368db2f6ce31b797fdf" class\="tgtSentence"\>System::DateTime::Subtract\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[div](../c-runtime-library/reference/div.md)|将一个整数除以另一个整数，从而返回商和余数|不适用。|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md), [\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|将 `double` 转换为指定长度的字符字符串|[\<caps:sentence id\="tgt60" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[exp、expf](../c-runtime-library/reference/exp-expf.md)|计算指数函数|[\<caps:sentence id\="tgt63" sentenceid\="81a65df6ac66cdc4a4b12c2f7e555487" class\="tgtSentence"\>System::Math::Exp\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)|  
|[fabs、fabsf](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|查找绝对值|[\<caps:sentence id\="tgt66" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md)、[\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|将 `double` 转换为具有小数点后指定位数的字符串|[\<caps:sentence id\="tgt69" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_finite](../c-runtime-library/reference/finite-finitef.md)|确定给定的双精度浮点值是否是有限的|[\<caps:sentence id\="tgt72" sentenceid\="8d081c50adeda3dde4cebab81a0b3583" class\="tgtSentence"\>System::Double::IsInfinity\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)|  
|[floor、floorf](../c-runtime-library/reference/floor-floorf-floorl.md)|查找小于或等于参数的最大整数|[\<caps:sentence id\="tgt75" sentenceid\="609db9ab0433b647d5350d3b965d70f9" class\="tgtSentence"\>System::Math::Floor\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.floor.aspx)|  
|[fmod、fmodf](../c-runtime-library/reference/fmod-fmodf.md)|查找浮点余数|[\<caps:sentence id\="tgt78" sentenceid\="127a04426267ccb17fb4b566ad56de9c" class\="tgtSentence"\>System::Math::IEEERemainder\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)|  
|[\_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|返回包含有关浮点类的信息的状态字|[System::Double::IsInfinity](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)、[System::Double::IsNegativeInfinity](https://msdn.microsoft.com/en-us/library/system.double.isnegativeinfinity.aspx)、[System::Double::IsPositiveInfinity](https://msdn.microsoft.com/en-us/library/system.double.ispositiveinfinity.aspx)、[System::Double::IsNan](https://msdn.microsoft.com/en-us/library/system.double.isnan.aspx)|  
|[\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)|为 IEEE 浮点异常调用用户定义的陷阱处理程序|不适用。|  
|[\_fpreset](../c-runtime-library/reference/fpreset.md)|重新初始化浮点数学包||  
|[frexp](../c-runtime-library/reference/frexp.md)|计算指数值|不适用。|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md)、[\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|将浮点值转换为字符字符串|[\<caps:sentence id\="tgt92" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[hypot、hypotf、hypotl、\_hypot、\_hypotf、\_hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|计算直角三角形的斜边|不适用。|  
|[\_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|检查非数值 \(NaN\) 的给定双精度浮点值|[\<caps:sentence id\="tgt97" sentenceid\="18f7dc07d0c506c23f2f7eb89262d274" class\="tgtSentence"\>System::Double::IsNan\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.isnan.aspx)|  
|[labs](../misc/labs-llabs.md)|返回 `long` 的绝对值|[\<caps:sentence id\="tgt100" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[ldexp](../c-runtime-library/reference/ldexp.md)|计算参数和 2<sup>exp</sup>（指定的幂）的结果|[\<caps:sentence id\="tgt103" sentenceid\="839e85fe5fb98e8520d40a703d06932b" class\="tgtSentence"\>System::Math::Pow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)|  
|[ldiv](../c-runtime-library/reference/ldiv-lldiv.md)|将一个 `long` 整数除以另一个整数，然后返回商和余数|不适用。|  
|[log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)|计算自然对数或以 10 为底的对数。|[System::Math::Log](https://msdn.microsoft.com/en-us/library/system.math.log.aspx)、[System::Math::Log10](https://msdn.microsoft.com/en-us/library/system.math.log10.aspx)|  
|[\_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|提取双精度浮点参数的指数值|不适用。|  
|[\_lrotl、\_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|将 `unsigned long int` 向左 \(`_lrotl`\) 或向右 \(`_lrotr`\) 移位|不适用。|  
|[\_matherr](../c-runtime-library/reference/matherr.md)|处理数学错误|不适用。|  
|[\_\_max](../c-runtime-library/reference/max.md)|返回两个值中较大的一个|[\<caps:sentence id\="tgt121" sentenceid\="6f9dcb228534c3e5b0013615b2b1d003" class\="tgtSentence"\>System::Math::Max\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.max.aspx)|  
|[\_\_min](../c-runtime-library/reference/min.md)|返回两个值中较小的一个|[\<caps:sentence id\="tgt124" sentenceid\="ff471983fc666dec7ba58b17a0bf76e6" class\="tgtSentence"\>System::Math::Min\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.min.aspx)|  
|[modf、modff](../c-runtime-library/reference/modf-modff-modfl.md)|将参数拆分为整数部分和分数部分|不适用。|  
|[nan、nanf、nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|返回 quiet NaN 值|[\<caps:sentence id\="tgt129" sentenceid\="c251043405ffa73fe857c83428b58fdc" class\="tgtSentence"\>System::Double::NaN\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.nan.aspx)|  
|[\_nextafter](../c-runtime-library/reference/nextafter-functions.md)|返回下一个可表示的邻近值|不适用。|  
|[pow、powf](../c-runtime-library/reference/pow-powf-powl.md)|计算乘幂的值|[\<caps:sentence id\="tgt135" sentenceid\="839e85fe5fb98e8520d40a703d06932b" class\="tgtSentence"\>System::Math::Pow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)|  
|[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|根据指定格式将数据写入 `stdout`|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)、[System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)|  
|[rand](../c-runtime-library/reference/rand.md)、[rand\_s](../c-runtime-library/reference/rand-s.md)|获取伪随机数|[\<caps:sentence id\="tgt141" sentenceid\="00574fde17be9de3e07567ef5abe0110" class\="tgtSentence"\>System::Random 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.random.aspx)|  
|[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|舍入到最接近的整数（采用浮点格式）|[\<caps:sentence id\="tgt143" sentenceid\="1c04aeb4aeff1752cb65adabcee29f53" class\="tgtSentence"\>System::Math::Round\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)|  
|[\_rotl、\_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|将 `unsigned int` 向左 \(`_rotl`\) 或向右 \(`_rotr`\) 移位|不适用。|  
|[\_scalb](../c-runtime-library/reference/scalb.md)|以 2 的幂缩放参数|不适用。|  
|[scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|乘以 `FLT_RADIX` 的整数幂|不适用。|  
|[scanf, wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|按照指定的格式从 `stdin` 中读取数据并将数据写入指定的位置|[System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)、[System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)|  
|[\_set\_controlfp](../c-runtime-library/reference/set-controlfp.md)|设置新的控制字值|不适用。|  
|[sin、sinf、sinh、sinhf](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|计算正弦或双曲正弦|[System::Math::Sin](https://msdn.microsoft.com/en-us/library/system.math.sin.aspx)、[System::Math::Sinh](https://msdn.microsoft.com/en-us/library/system.math.sinh.aspx)|  
|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|计算平方根|[\<caps:sentence id\="tgt162" sentenceid\="1a91af0bd8c63b4be64c7a0bec8dc8c4" class\="tgtSentence"\>System::Math::Sqrt\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.sqrt.aspx)|  
|[srand](../c-runtime-library/reference/srand.md)|初始化伪随机序列|[\<caps:sentence id\="tgt165" sentenceid\="00574fde17be9de3e07567ef5abe0110" class\="tgtSentence"\>System::Random 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.random.aspx)|  
|[\_status87, \_statusfp, \_statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|获取浮点状态字|不适用。|  
|[strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|将字符字符串转换为双精度值|[\<caps:sentence id\="tgt169" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[tan、tanf、tanh、tanhf](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|计算正切或双曲正切|[System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx)、[System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)