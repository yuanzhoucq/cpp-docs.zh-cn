---
title: Microsoft 宏汇编程序 BNF 语法
description: 针对 x64 的 MASM 的 BNF 说明。
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 29eae0b110f99f1f417e153f18aa2ac3aff5c69b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322822"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>Microsoft 宏汇编程序 BNF 语法

此页包含对 MASM 语法的 BNF 说明。 它作为参考主题的补充提供，并不保证其完整。 有关关键字、参数、操作等的完整信息，请参阅参考主题。

为了说明如何使用 BNF，下图显示了从非终止符*typedefDir*开始的 TYPEDEF 指令定义。

![MASM BNF 示例](media/bnf.png)

每个水平大括号下的条目都是终端（如**NEAR16**、 **NEAR32**、 **FAR16**和**FAR32**）或非终止符（如*限定符*、 *qualifiedType*、*距离*和*protoSpec*），可以进一步定义。 *TypedefDir*定义中的每个斜体非终止符也是 BNF 中的一个条目。 三个垂直点指示非终止符的分支定义，为了简单起见，此图并未说明这一点。

BNF 语法允许递归定义。 例如，语法使用 qualifiedType 作为 qualifiedType 的可能定义，这也是限定符定义的组成部分。 "|" 符号指定替代表达式之间的选择，例如*endOfLine* | *注释*。 双括号指定一个可选参数，例如⟦ *macroParmList* ⟧。 方括号实际上不会出现在源代码中。

## <a name="masm-nonterminals"></a>MASM 非终止符

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*endOfLine* | *注释*

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* = *immExpr* ;;

*addOp*\
&nbsp;&nbsp;&nbsp;&nbsp;+ |-

*aExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*术语* | *aExpr* && *术语*

*altId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;*charList*

*asmInstruction*\
&nbsp;&nbsp;&nbsp;&nbsp;*助记键*⟦ *exprList* ⟧

*assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**假设** *assumeList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| **假设没有**;;

*assumeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeRegister* | *assumeList* 、 *assumeRegister*\

*assumeReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* ： *assumeVal*

*assumeRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeSegReg* | *assumeReg*

*assumeSegReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentRegister* ： *assumeSegVal*

*assumeSegVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*frameExpr* | **无** | **错误**

*assumeVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **无** | **错误**

*bcdConst*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *sign* ⟧ *decNumber*

*binaryOp*\
&nbsp;&nbsp;&nbsp;&nbsp;= = |！ = |> = |< = |> |< |&

*bitDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitFieldId* ： *BitFieldSize* ⟦ = *constExpr* ⟧

*bitDefList*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitDef* | *bitDefList* 、⟦;;⟧ *bitDef*

*bitFieldId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*bitFieldSize*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*blockStatements*\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。继续** **。如果** *cExpr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。断开**⟦ **。如果** *cExpr* ⟧

*bool*\
&nbsp;&nbsp;&nbsp;&nbsp;**TRUE** | **FALSE**

*byteRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AL |AH |CL |CH |DL |DH |BL |BH |R8B |R9B |R10B |R11B |R12B |R13B |R14B |R15B

*cExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*aExpr* | *cExpr* || *aExpr*

*字符*\
&nbsp;&nbsp;&nbsp;&nbsp;除换行符（10）以外的序号在0–255范围内的任何字符。

*charList*\
&nbsp;&nbsp;&nbsp;&nbsp;*字符* | *charList*字符

*className*\
&nbsp;&nbsp;&nbsp;&nbsp;*字符串*

*commDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *nearfar* ⟧⟦ *langType* ⟧ *id* ： *commType*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦： *constExpr* ⟧

*commDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**通信**\
&nbsp;&nbsp;&nbsp;&nbsp;*commList* ;;

*注释*\
&nbsp;&nbsp;&nbsp;&nbsp;;*text* ;;

*commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**注释***分隔符*\
&nbsp;&nbsp;&nbsp;&nbsp;*文本*\
&nbsp;&nbsp;&nbsp;&nbsp;*文本* *分隔符* *文本*;;

*commList*\
&nbsp;&nbsp;&nbsp;&nbsp;*commDecl* | *commList* 、 *commDecl*

*commType*\
&nbsp;&nbsp;&nbsp;&nbsp;*类型* | *constExpr*

*常量*\
&nbsp;&nbsp; *&nbsp;&nbsp;* ⟦ *radixOverride* ⟧

*constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*contextDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUSHCONTEXT** *contextItemList* ; \
&nbsp;&nbsp;&nbsp;&nbsp;**POPCONTEXT** *contextItemList* ;;

*contextItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**假设** |  ** | **  |  ** | **

*contextItemList*\
&nbsp;&nbsp;&nbsp;&nbsp;*contextItem* | *contextItemList* 、 *contextItem*

*controlBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*whileBlock* | *repeatBlock*

*controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*controlIf* | *controlBlock*

*controlElseif*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ELSEIF** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧

*controlIf*\
&nbsp;&nbsp;&nbsp;&nbsp; **。如果**&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **。ELSE** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directiveList*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **。ENDIF** ;;

*协处理器*\
&nbsp;&nbsp;&nbsp;&nbsp;8087 |. 287 | 387 |。NO87

*crefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*crefOption* ;;

*crefOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **。CREF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.XCREF** ⟦ *idlist.txt* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOCREF** ⟦ *idlist.txt* ⟧

*cxzExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;|！ *expr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* = = expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* ！ = expr

*dataDecl*\
&nbsp;DB &nbsp;&nbsp;&nbsp;|DW |DD |DF |DQ |DT |*dataType* | *typeId*

*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *id* ⟧ *dataItem* ;;

*dataItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDecl* *scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag* *recordInstList*

*dataType*\
&nbsp;&nbsp;&nbsp;&nbsp;字节 |SBYTE |WORD |剑 |DWORD |SDWORD |FWORD |QWORD |SQWORD |TBYTE |OWORD |REAL4 |REAL8 |REAL10 |MMWORD |XMMWORD |YMMWORD

*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;0 |1 |2 |3 |4 |5 |6 |7 |8 |900

*decNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *decNumber* *decdigit*

*分隔符*\
&nbsp;除*whiteSpaceCharacter*之外的任何字符 &nbsp;&nbsp;&nbsp;

*数字*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *数字* *decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *数字*hexdigit

*指令*\
&nbsp;&nbsp;&nbsp;&nbsp;*generalDir* | *segmentDef*

*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;*指令* | *directiveList* *指令*

*距离*\
&nbsp;&nbsp;&nbsp;&nbsp;*nearfar* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

*形式*\
&nbsp;&nbsp;&nbsp;&nbsp;形式*orOp* *e02* | *e02*

*e02*\
&nbsp;&nbsp;&nbsp;&nbsp;e02**和** *e03* | *e03*

*e03*\
&nbsp;&nbsp;&nbsp;&nbsp;**NOT** *e04* | *e04*

*e04*\
&nbsp;&nbsp;&nbsp;&nbsp;*e04* *relOp* *e05* | *e05*

*e05*\
&nbsp;&nbsp;&nbsp;&nbsp;*e05* *addOp* *e06* | *e06*

*e06*\
&nbsp;&nbsp;&nbsp;&nbsp;*e06* *mulOp* *e07* | *e06* *shiftOp* *e07* | *e07*

*e07*\
&nbsp;&nbsp;&nbsp;&nbsp;*e07* *addOp* *e08* | *e08*

*e08*\
&nbsp;&nbsp;&nbsp;&nbsp;**高** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LOW** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **HIGHWORD** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LOWWORD** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09*

*e09*\
&nbsp;&nbsp;&nbsp;&nbsp;**偏移** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SEG** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LROFFSET** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **类型** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **此** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09* **PTR** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09* ： *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e10*

*e10*\
&nbsp;&nbsp;&nbsp;&nbsp;*e10* 。 *e11*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e10* ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *e11*

*e11*\
&nbsp;&nbsp;&nbsp;&nbsp;（ *expr* ） \
&nbsp;&nbsp;&nbsp;&nbsp;|⟦ *expr* ⟧ \
&nbsp;| **宽度** *id* &nbsp;&nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;| **掩码** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **大小** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZEOF** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **长度** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LENGTHOF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;| *字符串*\
&nbsp;&nbsp;&nbsp;&nbsp;| *常量*\
&nbsp;&nbsp;&nbsp;&nbsp;| *类型*\
&nbsp;&nbsp;&nbsp;&nbsp;| *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister*\
&nbsp;| *注册*&nbsp;&nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST** （ *expr* ）

*echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ECHO**\
&nbsp;&nbsp;&nbsp;&nbsp;*arbitraryText* ; \
%**OUT** *arbitraryText* ; \

*elseifBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*elseifStatement* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \

*elseifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**ELSEIF** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIF** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIFI** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDN** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDNI** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

*endDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**END** ⟦ *immExpr* ⟧;;

*endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **ENDP** ;;

*endsDir*\
*&nbsp;&nbsp;* &nbsp;&nbsp;**结束**;

*equDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*textMacroId* **等于** *equType* ;;

*equType*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr* | *textLiteral*

*errorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*errorOpt* ;;

*errorOpt*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ERR** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRE** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNZ** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRB** *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNB** *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRDEF** *id* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNDEF** *id* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRDIF** *textItem* ， *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRDIFI** *textItem* ， *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRIDN** *textItem* ， *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRIDNI** *textItem* ， *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERR1** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERR2** ⟦ *textItem* ⟧

*exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。退出**&nbsp;&nbsp;&nbsp;&nbsp;⟦ *expr* ⟧;;

*exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;： EXITM |EXITM *textItem*

*指数*\
&nbsp;&nbsp;&nbsp;&nbsp;E ⟦ *sign* ⟧ *decNumber*

*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHORT** *e05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。键入**形式 \
&nbsp;&nbsp;&nbsp;&nbsp;| **OPATTR** *形式*\
&nbsp;&nbsp;&nbsp;&nbsp;| *形式*

*exprList*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprList* ， *expr*

*externDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *Id* ⟦（ *altId* ）⟧： *externType*

*externDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*externKey* *externList* ;;

*externKey*\
&nbsp;&nbsp;&nbsp;&nbsp;**EXTRN** | **EXTERN** | **EXTERNDEF**

*externList*\
&nbsp;&nbsp;&nbsp;&nbsp;*externDef* | *externList* 、⟦;;⟧ *externDef*

*externType*\
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *qualifiedType*

*fieldAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*fieldInit*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *initValue* ⟧ |*structInstance*

*fieldInitList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fieldInit* | *fieldInitList* 、⟦;;⟧ *fieldInit*

*fileChar*\
&nbsp;&nbsp;&nbsp;&nbsp;*分隔符*

*fileCharList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileChar* | *fileCharList* *fileChar*

*fileSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileCharList* | *textLiteral*

*flagName*\
&nbsp;&nbsp;&nbsp;&nbsp;**零？** | **携带？** | **溢出？** | **符号？** | **奇偶校验？**

*floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *sign* ⟧ *decNumber* 。 ⟦ *decNumber* ⟧⟦*指数*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *位数*R |*数字*r

*forcDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**强制** | **IRPC**

*forDir*\
 | **IRP** **的**&nbsp;&nbsp;&nbsp;&nbsp;

*forParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ⟦： *forParmType* ⟧

*forParmType*\
&nbsp;&nbsp; **&nbsp;&nbsp;请求**|= *textLiteral*

*fpuRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**ST** *expr*

*frameExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;**SEG** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DGROUP** ： *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister* ： *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *id*

*generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelDir* | *segOrderDir* | *nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *includeLibDir* | *commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *groupDir* | *assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structDir* | *recordDir* | *typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externDir* | *publicDir* | *commDir* | *protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *equDir* |= Dir |*textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *contextDir* | *optionDir* | *processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *titleDir* | *pageDir* | *listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *crefDir* | *echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ifDir* | *errorDir* | *includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroDir* | *macroCall* | *macroRepeat* | *purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroWhile* | *macroFor* | *macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;| *aliasDir*

*gpRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AX |EAX |CX |ECX |DX |EDX |BX |EBX |DI |EDI |SI |ESI |最佳实践 |EBP |SP |ESP |RSP |R8W |R8D |R9W |R9D |R12D |R13W |R13D |R14W |R14D

*groupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*groupId* **GROUP** *segIdList*

*groupId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*hexdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;b |c |d |e |f |A |B |C |D |E |果

*id*\
&nbsp;&nbsp;&nbsp;&nbsp;标识符的第一个字符可以是大写或小写字母字符（`[A–Za-z]`），也可以是以下四个字符中的任何一种： `@ _ $ ?` 剩余字符可以是这些相同字符中的任何一个，也可以是十进制数字（`[0–9]`）。 最大长度为247个字符。

*idlist.txt*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *idlist.txt* ， *id*

*ifDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ifStatement* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \
&nbsp;&nbsp;&nbsp; **&nbsp;⟦;;** \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* ⟧; \

*ifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**是否**为*constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIF** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIFI** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDN** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDNI** *textItem* ， *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**包含** *fileSpec* ;;

*includeLibDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**INCLUDELIB** *fileSpec* ;;

*initValue*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *字符串*\
&nbsp;&nbsp;&nbsp;&nbsp;|？ \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** （ *scalarInstList* ） \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *bcdConst*

*inSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *labelDef* ⟧ *inSegmentDir*

*inSegDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*inSegDir* | *inSegDirList* *inSegDir*

*inSegmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*说明*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *procDir* ⟦ *LocalDirList* ⟧⟦ *inSegDirList* ⟧ *endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*

*instrPrefix*\
&nbsp;&nbsp;&nbsp;&nbsp;**代表** | **REPE** | **REPZ** | **REPNE** | **REPNZ** | **锁**

*说明*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrPrefix* ⟧ *asmInstruction*

*invokeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* ：： *register* | *expr* | **ADDR** *expr*

*invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**调用** *expr* ⟦，⟦;;⟧ *invokeList* ⟧;;

*invokeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*invokeArg* | *invokeList* 、⟦;;⟧ *invokeArg*

*关键字*\
&nbsp;任何保留字 &nbsp;&nbsp;&nbsp;。

*keywordList*\
&nbsp;&nbsp;&nbsp;&nbsp;*关键字* | *关键字* *keywordList*

*labelDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ： |*id* ：： |@@:

*labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **标签** *qualifiedType* ;;

*langType*\
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **PASCAL** | **FORTRAN** | **BASIC** | **SYSCALL** | **STDCALL**

*listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*listOption* ;;

*listOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **。列出**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.XLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.SFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.TFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTMACROALL** |  **.LALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLISTMACRO** |  **.SALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTMACRO** |  **.XALL**\

*localDef*\
&nbsp;&nbsp;&nbsp;&nbsp;**本地** *idlist.txt* ;;

*localDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**本地** *parmList* ;;

*localDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDir* | *localDirList* *localDir*

*localList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDef* | *localList* *localDef*

*macroArg*\
 % *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;|%*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;|%*macroFuncId* （ *macroArgList* ） \
&nbsp;&nbsp;&nbsp;&nbsp;| *字符串*\
&nbsp;&nbsp;&nbsp;&nbsp;| *arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;|< *arbitraryText* >

*macroArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroArg* | *macroArgList* 、 *macroArg*

*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *localList* ⟧ *macroStmtList*

*macroCall*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* *macroArgList* ; \
&nbsp;&nbsp;&nbsp;&nbsp;| *id* （ *macroArgList* ）

*macroDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **宏**⟦ *macroParmList* ⟧; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFor*\
&nbsp;&nbsp;&nbsp;&nbsp;*forDir* *ForParm* ，< *macroArgList* >; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;*forcDir* *id* 、 *textLiteral* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFuncId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroProcId* | *macroFuncId*

*macroIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroId* | *macroIdList* 、 *macroId*

*macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*macroParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ⟦： *parmType* ⟧

*macroParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroParm* | *macroParmList* 、⟦;;⟧ *macroParm*

*macroProcId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*macroRepeat*\
&nbsp;&nbsp;&nbsp;&nbsp;*repeatDir* *constExpr* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroStmt*\
&nbsp;&nbsp;&nbsp;&nbsp;*指令* \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;|： *macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;| **GOTO**\
&nbsp;&nbsp;&nbsp;&nbsp;*macroLabel*

*macroStmtList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroStmt* ; \
&nbsp;&nbsp;&nbsp;&nbsp;| *macroStmtList* *macroStmt* ; \

*macroWhile*\
&nbsp;&nbsp;&nbsp;&nbsp;**时**， *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;**所有** | **无** | **NOTPUBLIC**

*memOption*\
&nbsp;&nbsp; **&nbsp;&nbsp;小 | ** **中型** ** | ** **精简** | **大规模** | 大规模 ** | **

*助记键*\
&nbsp;&nbsp;&nbsp;&nbsp;指令名称。

*modelDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。模型**\
&nbsp;&nbsp;&nbsp;&nbsp;*memOption* ⟦， *modelOptlist* ⟧;;

*modelOpt*\
&nbsp;&nbsp;&nbsp;&nbsp;*langType* | *stackOption*

*modelOptlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelOpt* | *modelOptlist* 、 *modelOpt*

*模块*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directiveList* ⟧ *endDir*

*mulOp*\
&nbsp;&nbsp;&nbsp;&nbsp;\* |/ |**MOD**

*nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**名称**\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ; \

*nearfar*\
&nbsp;&nbsp;&nbsp;&nbsp;**接近** | 

*nestedStruct*\
&nbsp;&nbsp;&nbsp;&nbsp;*structHdr* ⟦ *id* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;**结束**&nbsp;&nbsp;&nbsp;; \

*offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*offsetDirType* ;;

*offsetDirType*\
&nbsp;&nbsp;&nbsp;&nbsp;**甚至** | **ORG** *immExpr* | **ALIGN** ⟦ *constExpr* ⟧

*offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;**组** | **段** | 

*oldRecordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ |*oldRecordFieldList* 、⟦ *constExpr* ⟧

*optionDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**选项** *optionList* ;;

*optionItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**CASEMAP** ： *mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DOTNAME** | **NODOTNAME**\
&nbsp;&nbsp;&nbsp;&nbsp;| **模拟器** | **NOEMULATOR**\
&nbsp;&nbsp;&nbsp;&nbsp;| **尾声**： *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;| **语言**： *langType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LJMP**
| **NOLJMP**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOKEYWORD** ： < *keywordList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOSIGNEXTEND**\
&nbsp;&nbsp;&nbsp;&nbsp;| **偏移**： *offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDMACROS** | **NOOLDMACROS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDSTRUCTS** | **NOOLDSTRUCTS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **PROC** ： *oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;| **序言**： *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **READONLY** | **NOREADONLY**\
&nbsp;&nbsp;&nbsp;&nbsp;| **范围** | **NOSCOPED**\
&nbsp;&nbsp;&nbsp;&nbsp;| **段**： *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** ： bool

*optionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*optionItem* | *optionList* 、⟦;;⟧ *optionItem*

*optText*\
&nbsp;&nbsp;&nbsp;&nbsp;， *textItem*

*orOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**或** | **XOR**

*oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;**公共** | **私有** | **导出**

*pageDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PAGE** ⟦ *pageExpr* ⟧;;

*pageExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;\+ |⟦ *pageLength* ⟧⟦， *pageWidth* ⟧

*pageLength*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*pageWidth*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*parm*\
&nbsp;&nbsp;&nbsp;&nbsp;*parmId* ⟦： *qualifiedType* ⟧ |*parmId* ⟦ *constExpr* ⟧⟦： *qualifiedType* ⟧

*parmId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*parmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*parm* | *parmList* 、⟦;;⟧ *parm*

*parmType*\
&nbsp;&nbsp; **&nbsp;&nbsp;请求**|= *textLiteral* | **VARARG**

*pOptions*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦*距离*⟧⟦ *langType* *⟧⟦ oVisibility* ⟧

*主*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* *BinaryOp* *expr* | *flagName* | *expr*

*procDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **PROC**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *pOptions* ⟧⟦ < *macroArgList* > ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *usesRegs* ⟧⟦ *procParmList* ⟧

*处理器*\
&nbsp;&nbsp;&nbsp;&nbsp;| 386 |. 486 |. .486P \
&nbsp;&nbsp;&nbsp;&nbsp;| 586 | .586P 686 | .686P |. 387

*processorDir*\
&nbsp;*处理器*&nbsp;&nbsp;&nbsp;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *协处理器*;;

*procId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*procItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*instrPrefix* | *dataDir* | *labelDir* | *offsetDir* | *generalDir*

*procParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧ *parmList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧ *parmId* ： VARARG ⟧

*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *id* ⟧： *qualifiedType*

*protoArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧ *protoList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧⟦ *id* ⟧： VARARG ⟧

*protoList*\
&nbsp;&nbsp;&nbsp;&nbsp;*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protoList* ，⟦;;⟧ *protoArg*

*protoSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦*距离*⟧⟦ *langType* *⟧⟦ protoArgList ⟧ |* *typeId*

*protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **PROTO** *protoSpec*

*pubDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *id*

*publicDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUBLIC** *pubList* ;;

*pubList*\
&nbsp;&nbsp;&nbsp;&nbsp;*pubDef* | *pubList* 、⟦;;⟧ *pubDef*

*purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**清除** *macroIdList*

*qualifiedType*\
&nbsp;*类型*&nbsp;&nbsp;&nbsp;|⟦*距离*⟧ **PTR** ⟦ *qualifiedType* ⟧

*限定符*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **PROTO** *protoSpec*

*引用*\
&nbsp;&nbsp;&nbsp;&nbsp;"|"

*qwordRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;RAX |RCX |RDX |RBX |RDI.TPL |RSI |RBP |R8 |R9 |R10 |R11 |R12 |R13 |R14 |R15

*radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。基数** *constExpr* ;;

*radixOverride*\
&nbsp;&nbsp;&nbsp;&nbsp;h |o |问 |t |y |H |O |问 |T |误差

*recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* { *oldRecordFieldList* } |*recordTag* < *oldRecordFieldList* >

*recordDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* **记录** *bitDefList* ;;

*recordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ |*recordFieldList* 、⟦;;⟧⟦ *constExpr* ⟧

*recordInstance*\
 {⟦;; ⟧ *recordFieldList* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;|< *oldRecordFieldList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** （ *recordInstance* ）

*recordInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordInstance* | *recordInstList* 、⟦;;⟧ *recordInstance*

*recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*注册*\
&nbsp;&nbsp;&nbsp;&nbsp;*specialRegister* | *gpRegister* | *byteRegister* | *qwordRegister* |  *fpuRegister* | *SIMDRegister* | *segmentRegister*

*regList*\
&nbsp;&nbsp;&nbsp;&nbsp;*注册* | *regList* *register*

*relOp*\
&nbsp;&nbsp;&nbsp;&nbsp;EQ |NE |LT |LE |GT |串联

*repeatBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **。重复**; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;;untilDir ;;

*repeatDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**重复** | **REPT**

*scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*initValue* | *scalarInstList* 、⟦;;⟧ *initValue*

*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;**字节** | **WORD** | **DWORD** | **段落** | "**页**

*segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;**公共** | **堆栈** | *ConstExpr* **上的** **公共** | **内存** | **PRIVATE**

*segDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。代码**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。数据**\
&nbsp;&nbsp;&nbsp;&nbsp;|   **。数据？** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。CONST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。FARDATA**⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|   **。FARDATA？** ⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。STACK** ⟦ *constExpr* ⟧

*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*segIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segIdList* ， *segId*

*segmentDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentDir* ⟦ *inSegDirList* ⟧ | endsDir *simpleSegDir ⟦ inSegDirList* *⟧* ⟦ endsDir *⟧*

*segmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId* **SEGMENT** ⟦ *segOptionList* ⟧;;

*segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** |  |  **GS** | **SS**

*segOption*\
&nbsp;&nbsp;&nbsp;&nbsp;*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *className*

*segOptionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segOption* | *segOptionList* *segOption*

*segOrderDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ALPHA** |  **。SEQ** |  **.DOSSEG** |  **.dosseg**

*segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;**只读**

*segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | **平**

*shiftOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **SHL**

*签名*\
 - |+

*simdRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;MM0 |MM1 |MM2 |MM3 |MM4 |MM5 |MM6 |MM7 |xmmRegister |YMM0 |YMM1 |YMM2 |YMM3 寄存器 |YMM4 |YMM5 |YMM6 |YMM7 |YMM8 |YMM9 |YMM10 |YMM11 |YMM12 |YMM13 |YMM14 |YMM15

*simpleExpr*\
 （ *cExpr* ） |*主要*

*simpleSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segDir* ;;

*sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *类型* | *e10*

*specialChars*\
 : | . |⟦ |⟧ |( | )|< |> |{ | }\
&nbsp;&nbsp;&nbsp;&nbsp;|+ |- |/ |* |& |% | !\
&nbsp;&nbsp;&nbsp;&nbsp;|' |\ |= | ; |, |"\
&nbsp;&nbsp;&nbsp;&nbsp;| *whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *endOfLine*

*specialRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;CR0 |CR2 |CR3 |DR0 |DR1 |DR2 |DR3 |DR6 |DR7 |TR3 |TR4 |TR5 |TR6 |TR7

*stackOption*\
&nbsp;&nbsp;&nbsp;&nbsp;**NEARSTACK** | **FARSTACK**

*startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。启动**;;

*stext*\
&nbsp;&nbsp;&nbsp;&nbsp;*stringChar* | *stext* *stringChar*

*string*\
&nbsp;&nbsp;&nbsp;&nbsp;*引言*⟦ *stext* ⟧*引号*

*stringChar*\
&nbsp;&nbsp;&nbsp;&nbsp;*引言* *|* 除引号之外的任何字符。

*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structItem* ; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structBody* *structItem* ;;

*structDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag* *structHdr* ⟦ *fieldAlign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦、非**唯一**⟧; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;**结束**;

*structHdr*\
&nbsp;&nbsp;&nbsp;&nbsp;**STRUC** | **结构** | **联合**

*structInstance*\
 < ⟦ *fieldInitList* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;|{⟦;; ⟧⟦ *fieldInitList* ⟧⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** （ *structInstList* ） \

*structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*structInstance* | *structInstList* 、⟦;;⟧ *structInstance*

*structItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *nestedStruct*

*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*术语*\
&nbsp;&nbsp;&nbsp;&nbsp;*simpleExpr* |！ *simpleExpr*

*text*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | *文本*字符 |！ *字符* *文本* | *字符*|！*字符*

*textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* *textMacroDir* ;;

*textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | *textMacroId* |% *constExpr*

*textLen*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*textList*\
&nbsp;&nbsp;&nbsp;&nbsp;*textItem* | *textList* 、⟦;;⟧ *textItem*

*textLiteral*\
&nbsp;&nbsp;&nbsp;&nbsp;< *文本*>;;

*textMacroDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**CATSTR** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZESTR** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SUBSTR** *textItem* 、 *textStart* ⟦、 *textLen* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **INSTR** ⟦ *TextStart* 、⟧ *textItem* 、 *textItem*

*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*textStart*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*titleDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*titleType* *arbitraryText* ;;

*titleType*\
&nbsp;&nbsp;&nbsp;&nbsp;**标题** | 标题 | **SUBTTL**

*type*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *距离*\
&nbsp;&nbsp;&nbsp;&nbsp;| *数据类型*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId*

*typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*typeId* **TYPEDEF**限定符

*typeId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*untilDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。直到** *cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **.UNTILCXZ** ⟦ *cxzExpr* ⟧;;

*usesRegs*\
&nbsp;&nbsp;&nbsp;&nbsp;**使用** *regList*

*whileBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **。\**
&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ; \
&nbsp;&nbsp;&nbsp;&nbsp; **.ENDW**

*whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8，9，11–13，26，32

*xmmRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 |XMM1 |XMM2 |XMM3 |XMM4 |XMM5 |XMM6 |XMM7 |XMM8 |XMM9 |XMM10 |XMM11 |XMM12 |XMM13 |XMM14 |XMM15\

