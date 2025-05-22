# Reflexion: Kubernetes Deployment

## Warum ist ein Deployment in Kubernetes nicht einfach nur eine etwas andere Version von `docker run --restart=always`?

Ein Deployment verwaltet mehrere identische Pods, ermöglicht Updates, Rollbacks und Skalierung. `docker run` betrifft nur einen einzelnen Container.

---

## Was tut das Deployment, wenn ein Pod plötzlich verschwindet – und warum ist das nicht einfach nur Magie?

Es stellt fest, dass ein Pod fehlt, und erstellt automatisch einen neuen, um den gewünschten Zustand wiederherzustellen.

---

## Was konntest du beim Rolling Update mit `kubectl get pods -w` beobachten – und wie wird hier sichergestellt, dass es keinen kompletten Ausfall gibt?

Alte Pods werden schrittweise durch neue ersetzt. Erst wenn ein neuer Pod bereit ist, wird ein alter beendet.

---

## Wie sorgt der Kubernetes-Service dafür, dass dein Browser-Ping (über NodePort) den richtigen Pod trifft – selbst wenn sich gerade ein Update vollzieht?

Der Service verwendet Labels, um alle passenden Pods zu finden, und leitet Anfragen an verfügbare Pods weiter – auch während eines Updates.

---

## In der Deployment-YAML: Welche Angaben betreffen die Pod-Vorlage, und welche regeln das Verhalten des Deployments (z.B. Skalierung, Strategie)?

Die Pod-Vorlage ist unter `spec.template`. Angaben wie `replicas` und `strategy` regeln das Verhalten des Deployments.

---

## Was passiert mit den Pods, wenn du das Deployment löschst – und warum ist das Verhalten logisch?

Die Pods werden ebenfalls gelöscht, weil sie vom Deployment kontrolliert werden und nicht unabhängig existieren.
