---
title: Docker アプリケーションの設計
description: このガイドではマイクロサービスについて詳しく説明していないため、ここでそのトピックについての詳しいガイドへの参照を確認してください。
ms.date: 02/15/2019
ms.openlocfilehash: 535b6cefb7371014527032972ec27ebfe4b67ebc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644654"
---
# <a name="design-docker-applications"></a>Docker アプリケーションの設計

第 1 章では、コンテナーと Docker に関する基本的な概念を紹介しました。 その情報は、開始するために必要な基本レベルの情報です。 しかし、エンタープライズ アプリケーションは、複雑で、1 つのサービスやコンテナーではなく、複数のサービスで構成されることがあります。 こうしたオプションのユース ケースでは、サービス指向アーキテクチャ (SOA) や高度なマイクロサービスの概念とコンテナー オーケストレーションの概念などの追加の設計アプローチを理解する必要があります。 このドキュメントの範囲は、マイクロサービスだけでなく、Docker アプリケーションのライフサイクルにも限定されないので、マイクロサービス アーキテクチャについては詳しく説明しません。通常の SOA、バック グラウンド タスクまたはジョブ、またはモノリシック アプリケーション デプロイ アプローチでもコンテナーや Docker を使用できるためです。

**詳細** エンタープライズ アプリケーションとマイクロサービス アーキテクチャの詳細については、「[.NET マイクロサービス:コンテナー化された .NET アプリケーションのアーキテクチャ](../../microservices-architecture/index.md)」ガイドを参照してください。これも <https://aka.ms/MicroservicesEbook> からダウンロードできます。

しかし、アプリケーション ライフサイクルと DevOps に進む前に、アプリケーションを設計して構築する方法と、設計の選択肢について理解することが重要です。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](common-container-design-principles.md)
