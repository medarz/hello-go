
Build image:

gcloud container clusters create meetup-cluster --zone us-central1-a
gcloud container clusters get-credentials meetup-cluster --zone us-central1-a --project account-2-232416


docker build -t gcr.io/account-2-232416/hello-go:v1 .
docker push gcr.io/account-2-232416/hello-go:v1


kubectl create deployment hello-go --image=gcr.io/account-2-232416/hello-go:v1
kubectl scale deployment hello-go --replicas=3
kubectl expose deployment hello-go --type=LoadBalancer --port 80 --target-port 8080

