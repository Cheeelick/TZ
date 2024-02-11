Процесс запуска minikube + jenkins
Запускаем minikube в docker, с указаем на 4 потока 
  minikube start --cpus=4
После скачиваем готовый репозиторий helm от jenkins с artifacthub 
  helm repo add jenkins https://charts.jenkins.io
  helm repo update
Если мы запустим данный репозиторий без инструмента helm, для того что бы развернуть наш helm chart в minikube, при запуске jobs jenkins будет выдавать ошибку: helm not found.
1. Что бы избежать неудач, было решено заменить образ jenkins на свой (файл есть а папке TZ).
2. Далее заменяем образ на свой для этого создал values файл для замены образа на свой.
Далее скачиваем jenkins и применяем файл values с помощью комманды
  helm install my_jenkins_helm jenkins/jenkins -f values.yaml
После удачного скачивания будем предлоджено запустить комманды для вывода пароля админа и запуска сервра jenkins
  kubectl exec --namespace default -it svc/my_jenkins_helm -c jenkins -- /bin/cat /run/secrets/additional/chart-admin-password && echo
  kubectl --namespace default port-forward svc/myjenkinshelm 8080:8080
