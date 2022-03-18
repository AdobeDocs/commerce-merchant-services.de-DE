---
title: Technische Hinweise zu Regeln
description: Technische Hinweise zur Verwendung von Live-Suchregeln
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Technische Hinweise zu Regeln

[!DNL Live Search] Regeln Trigger -Aktionen basierend auf einer Vielzahl von Abfragebedingungen und geben Händlern die Möglichkeit, das Sucherlebnis für verschiedene Szenarien zu gestalten.

Die aktuelle Version von [!DNL Live Search] -Regeln basieren auf der vom Käufer eingegebenen Abfragezeichenfolge und nicht auf dem Satz der zurückgegebenen Ergebnisse. Eine Abfragezeichenfolge kann alphanumerische Zeichen enthalten und die Groß-/Kleinschreibung wird ignoriert. Wie bei Facetten und Synonymen werden Regeln in gespeichert. `protobuf dynamo`. Zum Zeitpunkt der Abfrage ruft der Suchdienst Regeln über `grpc` Aufrufe an `search-admin-service`.
