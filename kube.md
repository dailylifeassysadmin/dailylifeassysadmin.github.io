A critical Kubernetes pod just crashed out of nowhere

When it happens, every second counts.

Here’s my 7-step debugging playbook:

👉 𝗦𝘁𝗲𝗽 𝟭: 𝗩𝗲𝗿𝗶𝗳𝘆 𝘁𝗵𝗲 𝗼𝗯𝘃𝗶𝗼𝘂𝘀
🔺 kubectl get pods -o wide → Is it actually crashed?
🔺 kubectl describe pod <pod-name> → Check restart count and status
🔺 kubectl get events –sort-by=’.lastTimestamp’ → Recent cluster events

👉 𝗦𝘁𝗲𝗽 𝟮: 𝗛𝘂𝗻𝘁 𝘁𝗵𝗿𝗼𝘂𝗴𝗵 𝗽𝗼𝗱 𝗹𝗼𝗴𝘀
🔺 kubectl logs <pod-name> –previous → Logs from crashed container
🔺 kubectl logs <pod-name> -f → Live logs from current container
🔺 kubectl logs <pod-name> -c <container-name> → Multi-container debugging

👉 𝗦𝘁𝗲𝗽 𝟯: 𝗖𝗵𝗲𝗰𝗸 𝗿𝗲𝘀𝗼𝘂𝗿𝗰𝗲 𝗰𝗼𝗻𝘀𝘂𝗺𝗽𝘁𝗶𝗼𝗻
🔺 kubectl top pods → CPU/Memory usage spikes
🔺 kubectl describe node <node-name> → Node resource pressure
🔺 kubectl get pods -o jsonpath=’{range .items[*]}{.metadata.name}{”\t”}{.spec.containers[0].resources}{”\n”}{end}’ → Resource limits

👉 𝗦𝘁𝗲𝗽 𝟰: 𝗜𝗻𝘃𝗲𝘀𝘁𝗶𝗴𝗮𝘁𝗲 𝘀𝘁𝗼𝗿𝗮𝗴𝗲 𝗶𝘀𝘀𝘂𝗲𝘀
🔺 kubectl get pvc → PersistentVolume claim status
🔺 kubectl describe pvc <pvc-name> → Volume mount failures
🔺 kubectl get events | grep -i volume → Storage-related events

👉 𝗦𝘁𝗲𝗽 𝟱: 𝗙𝗶𝗻𝗱 𝗻𝗲𝘁𝘄𝗼𝗿𝗸 𝗶𝘀𝘀𝘂𝗲𝘀
🔺 kubectl get svc → Service connectivity problems
🔺 kubectl describe endpoints <service-name> → Backend pod registration
🔺 kubectl get ingress → External access issues

👉 𝗦𝘁𝗲𝗽 𝟲: 𝗧𝗿𝗮𝗰𝗸 𝗰𝗼𝗻𝗳𝗶𝗴𝘂𝗿𝗮𝘁𝗶𝗼𝗻 𝗶𝘀𝘀𝘂𝗲𝘀
🔺 kubectl get configmap <cm-name> -o yaml → Configuration drift
🔺 kubectl get secret <secret-name> -o yaml → Missing secrets
🔺 kubectl describe deployment <deploy-name> → Deployment strategy failures

👉 𝗦𝘁𝗲𝗽 𝟳: 𝗥𝗲𝗮𝗹-𝘁𝗶𝗺𝗲 𝗱𝗲𝗯𝘂𝗴𝗴𝗶𝗻𝗴
🔺 kubectl exec -it <pod-name> – /bin/bash → Interactive debugging
🔺 kubectl port-forward <pod-name> 8080:80 → Direct pod access
🔺 kubectl get pods –watch → Real-time status monitoring

The key is following this systematically rather than randomly trying commands.

Whether you manage EKS, GKE, AKS, or on-premise clusters, this debugging flow works universally.

Save this post for your next 3 AM production incident.