kubctl

Steps
1- Create docker image and test
2- After you’re happy with the image, push it to gcr.io/project_id/img-name:img-version
3- Run next commands on google console. Creat cluster 
	$gcloud container clusters create clus-name --num-nodes 2 --machine-type n1-standard-1 --zone us-central1-f
4- deploy
	$kubectl run hello-node-app --image=gcr.io/test-feb2016/hello-node:0.1 --port=8080
5- Allow external traffic
	$kubectl expose deployment <deployment-name> --type="LoadBalancer"


Troubleshooting
* kubectl describe deployment wordpress
* kubectl logs -l app=wordpress web
* kubectl logs -l app=wordpress

Encrypt/decrypt files gcloud
https://cloud.google.com/container-builder/docs/securing-builds/use-encrypted-secrets-credentials
gcloud kms encrypt \
  --plaintext-file=secrets.json \
  --ciphertext-file=secrets.json.enc \
  --location=global \
  --keyring=[KEYRING-NAME] \
  --key=[KEY-NAME]


Create cloud sql user
$gcloud sql users create proxyuser cloudsqlproxy~% --instance=[INSTANCE_NAME] --password=[PASSWORD]

ssh into a container
$kubectl exec POD_NAME -c CONTAINR_NAME bash -ti --namespace=NAME_SPACE

Enable API and Configure IAM
export PROJECT=$(gcloud config get-value project)
export PROJECT_ID=$(gcloud projects list --filter id=${PROJECT} --format 'value(projectNumber)')
export DM_SA_EMAIL=${PROJECT_ID}@cloudservices.gserviceaccount.com
gcloud services enable deploymentmanager.googleapis.com runtimeconfig.googleapis.com
gcloud projects add-iam-policy-binding $PROJECT --member=serviceAccount:${DM_SA_EMAIL} --role roles/owner


Create a cluster
$ gcloud container clusters create "$CLUSTER" --zone "$ZONE" --num-nodes=3
OR
gcloud config set project PROJECT_ID
gcloud config set compute/zone us-central1-b
$ gcloud container clusters create --num-nodes=3

Create namespace
$ kubectl create namespace [name]

Retrive cluster credentials
$ gcloud container clusters get-credentials <cluster_name>

Get pods that contain name
$ pods=$(kubectl get pods --show-all --selector=job-name=partpodname --output=jsonpath={.items..metadata.name})


Get project name
$ export PROJECT=$(gcloud info --format='value(config.project)')

Get Cluster Name
$ export EAST_CLUSTER=$(gcloud container clusters list --filter="name:'east'" --format="value(name)")

Get ingress IP
$ export GKE_CENTRAL_INGRESS_IP=$(kubectl get ingress myapp-gke-central-ingress -o jsonpath='{.status.loadBalancer.ingress[0].ip}' --context gke-central)



export PROJECT=$(gcloud config get-value project)
export PROJECT_ID=$(gcloud projects list --filter id=${PROJECT} --format 'value(projectNumber)')
export DM_SA_EMAIL=${PROJECT_ID}@cloudservices.gserviceaccount.com
gcloud services enable deploymentmanager.googleapis.com runtimeconfig.googleapis.com
gcloud projects add-iam-policy-binding $PROJECT --member=serviceAccount:${DM_SA_EMAIL} --role roles/owner


export STUDENT_VM=$(gcloud compute instances list --format='value(name)' | grep student)
gcloud compute ssh $STUDENT_VM --zone=us-central1-f -- -L 8080:localhost:8080


Example of adding port to container
spec:
        containers:
        - name: beanstalkd
          image: kicka/beanstalkd:1.10
          imagePullPolicy: Always
          ports:
          - containerPort: 11300
          livenessProbe:
            tcpSocket:
              port: 11300
            initialDelaySeconds: 15
            timeoutSeconds: 5
          readinessProbe:
            tcpSocket:
              port: 11300
            initialDelaySeconds: 5
            timeoutSeconds: 1

========================

Excuse a command in container
spec:
        containers:
        - name: redis
          image: redis:3.2.1-alpine
          imagePullPolicy: Always
          ports:
          - containerPort: 6379
          livenessProbe:
            exec:
              command:
              - redis-cli
              - ping
            initialDelaySeconds: 5
            timeoutSeconds: 5
          readinessProbe:
            exec:
              command:
              - redis-cli
              - ping
            initialDelaySeconds: 5
            timeoutSeconds: 1


========================