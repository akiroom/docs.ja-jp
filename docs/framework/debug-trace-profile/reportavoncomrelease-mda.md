---
title: reportAvOnComRelease MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0ecb05dba70dc9c8aba7f04928fd0ab49c900c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873952"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
COM 相互運用を実行していて、COM の生呼び出しと組み合わせた `reportAvOnComRelease` または <xref:System.Runtime.InteropServices.Marshal.Release%2A> メソッドを使用しているときに、ユーザー参照カウントのエラーが原因で例外がスローされると、<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> マネージド デバッグ アシスタント (MDA) がアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 アクセス違反およびメモリ破損が発生します。  
  
## <a name="cause"></a>原因  
 COM 相互運用を実行していて、生の COM 呼び出しと組み合わせた <xref:System.Runtime.InteropServices.Marshal.Release%2A> または <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> メソッドを使用しているときに、ユーザー参照カウントのエラーが原因で例外がスローされることがあります。 通常、この例外は破棄されます。これは、破棄しないと CLR でアクセス違反が発生し、ダウンしてしまうためです。 このアシスタントが有効な場合は、そのような例外を単に破棄するのではなく、検出して報告できます。  
  
## <a name="resolution"></a>解像度  
 参照カウントのコードを調べてエラーを探します。また、オブジェクトのネイティブ クライアントに参照カウントのエラーがないかどうかも調べます。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 2 つのモードを利用できます。 `allowAv` 属性が `true` の場合、アシスタントは、ランタイムがアクセス違反を破棄しないようにします。 `allowAv` が `false` の場合 (既定)、ランタイムはアクセス違反を破棄しますが、例外がスローされて破棄されたことを通知する警告メッセージがユーザーに報告されます。  
  
## <a name="output"></a>出力  
 可能な場合、出力には COM インターフェイス ポインターの元の vtable が含まれます。 それ以外の場合は、情報メッセージが表示されます。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
