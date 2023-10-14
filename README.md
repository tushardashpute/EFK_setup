# EFK_setup


Installing Helm on Kubernetes

            $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
            $ chmod 700 get_helm.sh
            $ ./get_helm.sh

**Deploying an Elasticsearch Cluster with Helm**

            helm repo add elastic https://Helm.elastic.co
            curl -O https://raw.githubusercontent.com/elastic/Helm-charts/master/elasticsearch/examples/minikube/values.yaml
            helm install elasticsearch elastic/elasticsearch -f ./values.yaml 

The output you should be seeing looks something like this:

            helm install elasticsearch elastic/elasticsearch -f ./values.yaml 
            NAME: elasticsearch
            LAST DEPLOYED: Sat Oct 14 04:00:13 2023
            NAMESPACE: default
            STATUS: deployed
            REVISION: 1
            NOTES:
            1. Watch all cluster members come up.
              $ kubectl get pods --namespace=default -l app=elasticsearch-master -w
            2. Retrieve elastic user's password.
              $ kubectl get secrets --namespace=default elasticsearch-master-credentials -ojsonpath='{.data.password}' | base64 -d
            3. Test cluster health using Helm test.

**Deploying Kibana with Helm**

            helm install kibana elastic/kibana 

**Deploying Filebeat with Helm**

            helm install kibana elastic/filebeat 

Output will be like below:

            helm install filebeat elastic/filebeat
            NAME: filebeat
            LAST DEPLOYED: Sat Oct 14 09:36:50 2023
            NAMESPACE: default
            STATUS: deployed
            REVISION: 1
            TEST SUITE: None
            NOTES:
            1. Watch all containers come up.
              $ kubectl get pods --namespace=default -l app=filebeat-filebeat -w

Install Springboot Sample App:

            git clone https://github.com/tushardashpute/springboohello-CICD.git
            cd springboohello-CICD/
            kubectl apply -f springboot-deployment.yaml
            kubectl apply -f springboot-service.yaml

Login to Kibana using username elastic and password:

kubectl get secrets --namespace=default elasticsearch-master-credentials -ojsonpath='{.data.password}' | base64 -d


![image](https://github.com/tushardashpute/EFK_setup/assets/74225291/e9db8033-4b75-4606-a69f-42165844d623)


![image](https://github.com/tushardashpute/EFK_setup/assets/74225291/7c0fc6a8-095a-4d2f-993c-8b7b4a3dbcd3)

Added nginx helm chart as well :

 helm repo add bitnami https://charts.bitnami.com/bitnami
"bitnami" has been added to your repositories
[root@ip-172-31-16-18 ~]#
[root@ip-172-31-16-18 ~]# helm install mywebserver bitnami/nginx

![image](https://github.com/tushardashpute/EFK_setup/assets/74225291/bbdf87c6-ba5b-4896-94cc-cd09a3089066)

